# Desafio

## Descrição do Problema

Na **Mercado Libre** trabalhamos com `itens` de vendedores que os vendem através do nosso marketplace. O objetivo deste desafio é realizar uma aplicação que exponha uma _API_ que permita realizar algumas operações de _CRUD_ para cada uma dessas duas entidades com algumas regras de negócio sobre elas.

### Itens

Um item tem informações básicas sobre o artigo que será anunciado por nós.

#### Representação de um Item

A seguir, um exemplo de representação _JSON_ de um item:

```json
{
  "id": 10,
  "code": "SAM27324354",
  "title": "Tablet Samsung Galaxy Tab S7",
  "description": "Galaxy Tab S7 with S Pen SM-t733 12.4 polegadas e 4GB de memória RAM",
  "price": 150000,
  "stock": 3,
  "status": "ACTIVE",
  "created_at": "2020-05-10T04:20:33Z",
  "updated_at": "2020-05-10T05:30:00Z"
}
```

#### Regras sobre Itens

1. Os _ids_ devem ser gerados automaticamente.
2. Os campos `code`, `title`, `description`, `price`, `stock`, `photos` são obrigatórios.
3. O campo `code` deve ser único.
4. Os campos `status`, `created_at`, `updated_at` são gerados automaticamente pelo sistema. A API não deve permitir modificações neles.
5. O campo `status` pode ter os seguintes valores:

- `ACTIVE`: Um item que tem estoque disponível.
- `INACTIVE`: Um item cujo valor de estoque é zero (0).

#### Desafio

Usando a seguinte estrutura de `Item`, permita as seguintes funcionalidades. Para criar ou editar itens, considere as regras descritas anteriormente.

1. **Criar novos itens.**

_Request_:

```
POST v1/items
```

_Body_:

```json
{
  "code": "SAM27324354",
  "title": "Tablet Samsung Galaxy Tab S7",
  "description": "Galaxy Tab S7 with S Pen SM-t733 12.4 polegadas e 4GB de memória RAM",
  "price": 150000,
  "stock": 15
}
```

_Response_:

Você define a resposta, faz parte do desafio.

2. **Atualizar um item**

_Request_:

```
PUT v1/items/{id}
```

_Body_:

```json
{
  "code": "SAM27324354",
  "title": "Tablet Samsung Galaxy Tab S7",
  "description": "Galaxy Tab S7 with S Pen SM-t733 12.4 polegadas e 4GB de memória RAM",
  "price": 158000,
  "stock": 25
}
```

_Response_:

Você define a resposta, faz parte do desafio.

3. **Obter um item por ID**

Retorna o item correspondente ao _ID_.

_Request_:

```
GET v1/items/{id}
```

_Response_:

Você define a resposta, faz parte do desafio.

4. **Excluir Item**

Exclui o item correspondente ao _ID_.

_Request_:

```
DELETE v1/items/{id}
```

_Response_:

Você define a resposta, faz parte do desafio.

5. **Obter todos os itens (opcional: permitir filtragem por _Status_)**

Retorna os itens filtrados por _Status_ (opcional). Os resultados vêm organizados por data de atualização, do mais recente ao mais antigo. Deve dar a opção ao usuário de definir um limite de resultados na busca.

_Request_:

```
GET v1/items?status={status}&limit={limit}
```

Onde:

- `status`: É o filtro pelo estado do item; é um parâmetro opcional:

  - `Não especificado`: Retorna todos os itens, independentemente do valor do campo de estado
  - `ACTIVE`: Retorna os itens ativos
  - `INACTIVE`: Retorna os itens inativos

- `limit`: É o tamanho solicitado de resultados na página. É um parâmetro opcional, com valor padrão de 10, e valor máximo de 20.

_Response_:

A resposta deve seguir a seguinte estrutura de campos:

- `totalPages`: O número total de itens que contêm resultados para a busca feita.
- `data`: Um array com os objetos contendo os itens solicitados no request.

```json
{
  "totalPages": 1,
  "data": [
    {
    "id": 10,
    "code": "SAM27324354",
    "title": "Tablet Samsung Galaxy Tab S7",
    "description": "Galaxy Tab S7 with S Pen SM-t733 12.4 polegadas e 4GB de memória RAM",
    "price": 150000,
    "stock": 3,
    "status": "ACTIVE",
    "created_at": "2020-05-10T04:20:33Z",
    "updated_at": "2020-05-10T05:30:00Z"
    }
  ]
}
```

## Critérios de Avaliação

Esperamos que o código que você vai criar seja considerado por você como _"Pronto para Produção"_; por favor, use as boas práticas às quais você está acostumado em sua rotina de desenvolvimento de código.

Para a avaliação do seu código, esperamos que seja portátil. Esperamos que você nos forneça um comando para rodar facilmente no ambiente local a solução do problema.

Para o desenvolvimento do desafio, vamos utilizar Golang como linguagem.

Dentro dos critérios que vamos considerar ao revisar seu código, avaliaremos:

- Resolve o problema proposto
- Organização e estrutura do projeto
- Manutenibilidade
- Facilidade para fazer testes
- Valorizaremos adicionalmente se usar alguma arquitetura limpa (ex. arquitetura hexagonal).
