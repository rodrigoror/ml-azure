# Deploy de Modelo de Previsão com Endpoints Configurados

Este documento descreve, de forma detalhada, o processo para criar um modelo de previsão no Azure, configurar seus endpoints para inferência e organizar os arquivos no repositório.

---

## 1. Criação do Modelo de Previsão

### 1.1. Configuração do Ambiente no Azure Machine Learning
- Acesse o [Azure Portal](https://portal.azure.com) e entre no seu Workspace do Azure Machine Learning.
- Inicie um novo experimento utilizando **Automated Machine Learning**.
- Selecione e carregue os dados de treinamento, definindo o problema como **previsão** (regressão ou classificação conforme a necessidade).
- Configure os parâmetros do experimento (divisão de dados, métricas de avaliação, etc.) e execute o treinamento.
- Analise os resultados e escolha o modelo que melhor atende aos requisitos.

---

## 2. Configuração dos Endpoints

### 2.1. Realizando o Deploy do Modelo
- No Azure Machine Learning Studio, após a seleção do melhor modelo, clique na opção **Deploy**.
- Configure o deploy:
  - **Nome do Endpoint:** Exemplo: `modelo-previsao-endpoint`.
  - **Recursos:** Defina CPU, memória e outras configurações de acordo com a demanda.
- Conclua o deploy para gerar os endpoints necessários:
  - **Scoring URI:** URL para enviar requisições de previsão.
  - **Swagger URI:** URL para acessar a documentação da API.

### 2.2. Salvando a Configuração dos Endpoints
Crie um arquivo chamado `endpoint_config.json` com o seguinte conteúdo:
```json
{
  "endpointName": "modelo-previsao-endpoint",
  "scoringUri": "https://<seu-servico>.azurewebsites.net/score",
  "swaggerUri": "https://<seu-servico>.azurewebsites.net/swagger"
}
