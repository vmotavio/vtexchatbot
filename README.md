# BruceBot
[Demo](https://front.d2zbk2g76pq74b.amplifyapp.com/)

## O que é?   
Chatbot para marketplace com funcionalidades de acompanhamento de pedidos. 

## Objetivo   
Desenvolver um canal de comunicação baseado em Chatbot, genérico, que possa “plugar" em outros marketplaces (Exemplo: Mercado Livre).

## Equipe

### Líder da Equipe
Gabriel M. Dantas

### Equipe Front-End
| Membro | E-mail | Github |
|--- | --- | --- |
|Gabriel Moura Dantas| gabrielmd123@gmail.com| [mnegabriel](github.com/mnegabriel)
|Rafaela Souza Morais| crispim.rafaela@gmail.com|[rafaelasmorais](https://github.com/rafaelasmorais)
|Leslie Cespedes Gamarra	| leslita.scg@gmail.com |[leslitaS](https://github.com/leslitaS)

### Equipe Arquitetura
| Membro | E-mail | Github |
|--- | --- | --- |
|Anderson Carneiro Sousa |acarneirosousa@gmail.com| [a-cs](https://github.com/a-cs/)
|Alisson Rodrigo Santana dos Santos | rodrigoalisson33@gmail.com|[rodrigogus94](https://github.com/rodrigogus94)
|Gutierre Santos Pires | gutierre.pires@gmail.com|[gspires](https://github.com/gspires)
|Samuel Barbosa Costa da Silva | samuka1@gmail.com | [smkbarbosa](github.com/smkbarbosa)

### Equipe Back-End
| Membro | E-mail | Github |
|--- | --- | --- |
|Julie Barros Pessôa | pessoajjulie@gmail.com|[JuliePessoa](https://github.com/JuliePessoa)
|Fabricio Cavalcante Costa de Souza | fabricio.unix@gmail.com |[fcsouza](https://github.com/fcsouza)
|Otávio Vargas Moreira | vmotavio@gmail.com|[vmotavio](https://github.com/vmotavio)


## Metodologia de Desenvolvimento

### Sprint Backlog
Devido ao prazo de desenvolvimento do projeto, o backlog da sprint foi ajustado diariamente conforme a evolução dos estudos em cada ferramenta. 

### Dailys
No decorrer da semana foram realizadas _dailys_ para acompanhar o desenvolvimento do projeto, sempre às **22h**. O principal objetivo da reunião foi responder 3 perguntas:

* O que você tem feito desde ontem em direção a meta?
* O que você está planejando fazer amanhã em direção a meta?
* Você tem algum problema impedindo você de realizar seu objetivo em direção a meta?

### Retrospectiva de Sprint e Revisão de Sprint
A retrospectiva e revisão da sprint coincidiu com o dia da entrega do projeto à Gama Academy, onde foram expostos todas as ferramentas e trabalhando de forma integrada.  

## Arquitetura da Solução
![Arquitetura](https://github.com/smkbarbosa/chatbot-vtex-gama/blob/master/project-architecture.jpeg) 

Usando React.js no front-end foi desenvolvido uma solução que conecta a Amazon lex através do Amplify. O Front "conversa" com o cliente do marketplace e repassa as informações para o Amazon lex. O Amazon Lex interpreta as palavras do cliente e designa para o Amazon Lambda relacionado a intenção interpretada. Há uma função lambda para cada intenção. As funções lambda são responsáveis por fazer comunicação com a API do marketplace e requisitar as informações desejadas dos pedidos. No caso de cancelamento, a função Lambda específica também faz comunicação com o DynamoDB para salvar o motivo do cancelamento do pedido.

## Funcionalidades do Bot para o cliente do marketplace

### Rastreamento

Para que o cliente do marketplace tenha acesso ao rastreamento do pedido, é só iniciar a conversa com a palavra “rastreamento” e responder o BruceBot com o número do pedido.

### Cancelamento

O BruceBot também realiza cancelamentos para o cliente, é só iniciar a conversa com a palavra “cancelamento” e contar o motivo do cancelamento.

### Status

É possível também verificar o status do pedido, basta começar a conversa com a palavra “status” e informar o número do pedido.


## Funcionalidades do Bot para o marketplace

### Monitoramento e Alocação de Recurso via CloudWatch

Através do CloudWatch é possível ativar logs e definir métricas personalizadas de acordo com o interesse e limitação de orçamento do marketplace. Essas métricas são importante para acompanhar desempenho e custos dos recursos utilizados para o BruceBot. 
Pensando na relevância do limite de orçamento do marketplace, através do CloudWatch, também é possível criar alertas de limite de recursos para o cliente-marketplace.
Com o CloudWatch também é possível automatizar o planejamento de alocação de recurso com base nas métricas definidas, tanto para aumentar quanto para diminuir, ajudando a reduzir os custos.

### Análise de Custo

O levantamento de Custo foi realizado estipulando que cada usuário consumisse os 3 tipos de informação que o bot disponibiliza.
Para visualizar, [clique aqui](https://github.com/smkbarbosa/chatbot-vtex-gama/wiki/An%C3%A1lise-de-Custo)

### Benefícios

* Suporte da AWS  
* Segurança da identidade do cliente  
* Facilidade de processar linguagem natural com Lex  
* Fácil manutenção dos componentes  
* Redução do custo humano de atendimento ao cliente  
* Agilidade no atendimento ao cliente  

## Estrutura do Código no Github

*obs: A configuração do Amazon Lex não está disponível no github.

### Front

Linguagem: React.js     
Parte da aplicação responsável por receber informação do usuário do marketplace e se comunicar com o Amazon Lex.
[Comandos para rodar o front localmente](https://github.com/smkbarbosa/chatbot-vtex-gama/blob/master/front/README.md)

### Backend / src / Lambda 

Linguagem: Node.js    
Nesta pasta estão as três funções do AWS lambda responsáveis pela comunicação com API do marketplace e processar as informações recebidas do Amazon Lex.   
[Comandos para rodar o lambda localmente](https://github.com/smkbarbosa/chatbot-vtex-gama/blob/master/backend/src/lambda/trackingOrder/command.txt)


## Funcionalidades Futuras
* Fila de atendimento  
* Adicionar opções de busca de pedido por outras propriedades além do ID.
