# Projeto-de-Banco-de-Dados-E-commerce
## Introdução
Este é um projeto de banco de dados relacional para um sistema de E-commerce. O modelo foi desenvolvido para atender às necessidades de gerenciamento de clientes, pedidos, produtos, pagamentos, estoque, e outros aspectos essenciais para um ambiente de comércio eletrônico. O banco de dados segue as boas práticas de normalização e estruturação, garantindo escalabilidade, consistência e manutenção fácil.

## 📝Requisitos
* **Produto:**
  * Os Produtos são vendidos por uma unica pltaforma online. Contudo, estes podem ter vendedores distintod(terceiros).
  * Cada produto possui um fornecedor.
  * Um ou mais produtos podem compor um pedido.
 
* **Cliente:**
  * O cliente pode se cadastrar no site com seu CPF ou CNPJ.
  * O Endereço do Cliente irá determinar o valor do frete.
  * Um cliente pode realizar mais de um pedido. Este tem um periodo de carência para devolução do produto.
 
* **Refinamento:**
  * Cliente PJ e FF - Uma conte pode ser PJ e FP, mas não pode ter as duas informações.
  * Pagamento - pode ter cadastro mais de uma forma de pagamento.
  * Entrega - Possui status e código de rastreio.
    
    
  
## 🗃Estrutura do Banco de Dados
Abaixo está a descrição de cada tabela do modelo e seu papel no sistema:
### **1. Fornecedor**

* **Objetivo:** Gerenciar as informações dos fornecedores de produtos.

* **Campos:**
  * idFornecedor: Identificador único do fornecedor.
  * Razao Social: Nome da razão social do fornecedor.
  * CNPJ: Identificação fiscal do fornecedor.

### **2. Disponibilizando um produto**

* **Objetivo:** Relacionar fornecedores com os produtos que eles fornecem.

* **Campos:**
  * Fornecedor_idFornecedor: Chave estrangeira para a tabela Fornecedor.
  * Produto_idProduto: Chave estrangeira para a tabela Produto.

### **3. Estoque**

* **Objetivo:** Controlar os locais de armazenamento de produtos e suas quantidades.

* **Campos:**
  * idEstoque: Identificador único do estoque.
  * Local: Localização do estoque.

### **4. Produto_has_Estoque**

* **Objetivo:** Relacionar os produtos aos estoques onde estão armazenados e suas respectivas quantidades.

* **Campos:**
  * Produto_idProduto: Chave estrangeira para a tabela Produto.
  * Estoque_idEstoque: Chave estrangeira para a tabela Estoque.
  * Quantidade: Quantidade de produtos disponíveis no estoque.


### **5. Terceiro - vendedor**

* **Objetivo:** Gerenciar os vendedores terceiros que oferecem produtos no e-commerce.

* **Campos:**
  * idTerceiro: Identificador único do vendedor terceiro.
  * Razao Social: Nome da razão social do vendedor.
  * Local: Localização do vendedor.

### **6. Produto por vendedor (terceiro)**

* **Objetivo:** Relacionar os produtos vendidos por vendedores terceiros e suas respectivas quantidades.

* **Campos:**
  * Terceiro_idTerceiro: Chave estrangeira para a tabela Terceiro - vendedor.
  * Produto_idProduto: Chave estrangeira para a tabela Produto.
  * Quantidade: Quantidade de produtos oferecidos pelo vendedor.

### **7. Produto**

* **Objetivo:** Gerenciar as informações dos produtos disponíveis no e-commerce.

* **Campos:**
  * idProduto: Identificador único do produto.
  * Categoria: Categoria do produto.
  * Descrição: Detalhes sobre o produto.
  * Valor: Preço do produto.

### **8. Produto_Pedido**

* **Objetivo:** Relacionar os produtos aos pedidos realizados pelos clientes.

* **Campos:**
  * Produto_idProduto: Chave estrangeira para a tabela Produto.
  * Pedido_idPedido: Chave estrangeira para a tabela Pedido.
  * Quantidade: Quantidade do produto no pedido.

### **9. Pedido**

* **Objetivo:** Gerenciar os pedidos realizados pelos clientes.

* **Campos:**
  * idPedido: Identificador único do pedido.
  * Status do pedido: Estado atual do pedido (ex.: "Pendente", "Enviado", "Cancelado").
  * Descrição: Detalhes adicionais do pedido.
  * Cliente_idCliente: Chave estrangeira para a tabela Cliente.

### **10. Cliente**

* **Objetivo:** Armazenar as informações dos clientes cadastrados no sistema.

* **Campos:**
  * idCliente:** Identificador único do cliente.
  * Nome: Nome completo do cliente.
  * Tipo_Cliente: Identificação do cliente como PF (Pessoa Física) ou PJ (Pessoa Jurídica).
  * Telefone: Contato do cliente.
  * CPF_CNPJ: Identificação fiscal do cliente.

### **11. Endereço**

* **Objetivo:** Gerenciar os endereços dos clientes e suas informações detalhadas.

* **Campos:**
  * idEndereco: Identificador único do endereço.
  * Logradouro, Número, Complemento, Bairro, Cidade, Estado: Dados do endereço.
  * Frete: Valor do frete associado ao endereço.
  * Cliente_idCliente: Chave estrangeira para a tabela Cliente.

### **12. Pagamento**

* **Objetivo:** Gerenciar as informações dos pagamentos realizados pelos clientes.

* **Campos:**
  * idPagamento: Identificador único do pagamento.
  * Forma_Pagamento: Meio de pagamento utilizado (ex.: cartão de crédito, boleto).
  * Data_pagamento: Data do pagamento.
  * Pedido_idPedido: Chave estrangeira para a tabela Pedido.
  * Pedido_Cliente_idCliente: Chave composta para garantir referência ao cliente que fez o pedido.

### **13. Entrega**

* **Objetivo:** Gerenciar as entregas dos pedidos aos clientes.

* **Campos:**
  * idEntrega: Identificador único da entrega.
  * Status_Entrega: Estado atual da entrega (ex.: "Em transporte", "Entregue").
  * Codigo_rastreio: Código de rastreamento da entrega.
  * Previsão_entrega: Data estimada para a entrega.
  * Saida_Entrega: Data de saida da entraga.
  * Pedido_idPedido: Chave estrangeira para a tabela Pedido.
 
 ## 🛠**Modelo**
 * **Ferramenta utilizada:**
   * MySQL WorkBench.

[Ecesse aqui o Modelo](https://github.com/siqueirago/Projeto-de-Banco-de-Dados---E-commerce/blob/main/Modelo_ERR.md)
 
 
 ## Considerações Finais

Este modelo foi projetado para oferecer flexibilidade e eficiência no gerenciamento de um e-commerce. Caso tenha dúvidas ou sugestões, sinta-se à vontade para contribuir com o repositório!
