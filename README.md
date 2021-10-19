# Aula MBA FIAP Kafka (Hands On)

## Pré-requisitos:
1- Java (JDK ou JRE)

2- Git

3- Postman ou cURL

##  1- Cloud Karafka

### Fazer o registro no cloud karafka

1 - Acessar https://customer.cloudkarafka.com/signup

2 - Preencher com seu e-mail

3 - Acesse seu e-mail e click no link

4 - Termine de preencher o formulário do Karafka

### Criar sua instância
1 - Clique no botão Create New Instance

2 - Certifique-se de escolher o plano Developer Duck, e preencha o nome da instância. Em seguida, clique em "Select Region"

3 - Escolha US-EAST-1 e clique em "Preview".

4 - Clique em "Create Instance"

### Criar tópico
1 - Da tela de administração da instância, clique em "TOPICS" no menu lateral

2 - preencha o sufixo "events" no nome do tópico.

3 - Clique em "Create

##  2- Conduktor
### Instalação e configuração
1 - Acesse https://www.conduktor.io/download/

2 - Faça o download e a instalação

3- Execute a aplicação e clique em  "New Kafka Cluster"

4 - Escolha um nome para nome de seu cluster

5 - Em Bootstrap servers, coloque:
>dory-01.srvs.cloudkafka.com:9094

6 - Preencha "Additional Properties" com os dados abaixo:

> security.protocol=SASL_SSL
sasl.mechanism=SCRAM-SHA-256
sasl.jaas.config=org.apache.kafka.common.security.scram.ScramLoginModule required username="USER" password="PASS";

Onde USER é o usuário da sua instância do Cloud Karafka, e a senha do mesmo.

7 - Clique em "Save"

### Criando o consumidor
1- Clique na representação do seu Cluster, no menu lateral

2 - Clicar em Consumers

3 - Clique no dropbox com o texto "Pick a Topic to inspect its data"

4 - Selecione o tópico que possui o sufixo "events" (o tópico que acabou de criar)

5 - Clique em "Start"

## 3- Credit Event Producer
1 - Rode localmente o seguinte comando

> git clone https://github.com/the-sidh/poc-kafka-fiap.git

2 - Editar o arquivo **resources/application.yml**  no seu editor favorito.

3 - Na linha 15, substitua o username e passwords pelos da sua instância

4 - Na linha 17, substitua o nome do tópico pelo seu

5 - Salve o arquivo

6 - No console, de dentro do diretório do projeto, execute:

> ./gradlew bootRun

## 4 - Postman
1 - Abra o postman

2 - Clique em Import

3 - Selecione o arquivo que está dentro da pasta postman, do projeto clonado do GitHub

4 - Faça envio do seu evento e acompanhe o recebimento no consumidor do Conduktor!
