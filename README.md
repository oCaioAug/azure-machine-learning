# Fundamentos de Inteligência Artificial - Laboratório de Machine Learning

Este repositório contém o passo a passo para o laboratório "Fundamentos de IA: Aprendizado de Máquina" da Microsoft. Este laboratório explora como criar, treinar e avaliar um modelo de aprendizado de máquina usando o ambiente do Azure Machine Learning.

## Pré-requisitos

- **Conta do Azure**: Este laboratório utiliza o Azure Machine Learning, portanto, você deve ter uma conta no Azure.
- **Computador ou VM com acesso à internet**.
- **Permissão para criar recursos no Azure**.

## Sumário

1. [Configuração do Ambiente](#1-configuração-do-ambiente)
2. [Criação e Configuração do Workspace do Azure Machine Learning](#2-criação-e-configuração-do-workspace-do-azure-machine-learning)
3. [Importação de Dados](#3-importação-de-dados)
4. [Preparação de Dados](#4-preparação-de-dados)
5. [Treinamento do Modelo](#5-treinamento-do-modelo)
6. [Avaliação do Modelo](#6-avaliação-do-modelo)
7. [Implantação do Modelo](#7-implantação-do-modelo)
8. [Teste do Modelo Implantado](#8-teste-do-modelo-implantado)
9. [Conclusão](#conclusão)

---

### 1. Configuração do Ambiente

- Abra o portal do Azure ([https://portal.azure.com](https://portal.azure.com)).
- Crie uma nova **máquina virtual (VM)** se necessário ou acesse o **Azure Machine Learning Studio**.

### 2. Criação e Configuração do Workspace do Azure Machine Learning

1. Acesse o **Azure Machine Learning Studio** em [https://ml.azure.com](https://ml.azure.com).
2. Clique em **Create a new workspace** e preencha os campos necessários:
   - **Subscription**: Selecione sua assinatura.
   - **Resource Group**: Crie um novo grupo de recursos ou escolha um existente.
   - **Workspace Name**: Insira um nome exclusivo para o workspace.
   - **Region**: Escolha uma região próxima para reduzir a latência.
3. Clique em **Review and Create** para finalizar a configuração.

### 3. Importação de Dados

1. No **Azure Machine Learning Studio**, vá para a seção **Datasets**.
2. Clique em **+ Create Dataset** e selecione **From local files**.
3. Faça upload do arquivo de dados que será utilizado para o treinamento do modelo.
4. Nomeie o dataset, configure o tipo de arquivo e defina o schema conforme necessário.

### 4. Preparação de Dados

1. Acesse o **Designer** no **Azure Machine Learning Studio**.
2. Arraste o dataset importado para a área de trabalho.
3. Utilize módulos de preparação, como:
   - **Clean Missing Data**: Remova ou substitua valores ausentes.
   - **Select Columns in Dataset**: Escolha colunas relevantes.
   - **Normalize Data**: Normalize ou padronize os dados para melhorar a eficiência do modelo.

### 5. Treinamento do Modelo

1. No **Designer**, vá até a seção de módulos de **Machine Learning**.
2. Arraste o módulo de **Split Data** para dividir o dataset em dados de treino e teste.
3. Arraste o módulo de algoritmo (como **Two-Class Logistic Regression**) e conecte-o aos dados de treino.
4. Arraste o módulo **Train Model** e conecte-o ao algoritmo e aos dados de treino.
5. Execute o treinamento.

### 6. Avaliação do Modelo

1. No **Designer**, adicione o módulo **Score Model** para verificar a precisão dos dados de teste.
2. Conecte o **Score Model** aos dados de teste e ao modelo treinado.
3. Adicione o módulo **Evaluate Model** para analisar métricas de desempenho, como precisão e recall.
4. Execute o pipeline para avaliar o modelo.

### 7. Implantação do Modelo

1. Após a avaliação, vá para a seção de **Models** e selecione o modelo treinado.
2. Clique em **Deploy** e configure o endpoint para acessar o modelo via API.
3. Após a implantação, você verá o **endpoint** e a **chave de API** para testar o modelo.

### 8. Teste do Modelo Implantado

Para testar o endpoint do modelo implantado, envie uma solicitação POST para o endpoint usando o JSON abaixo como o payload.

#### Exemplo de JSON de Entrada:

```json
{
  "input_data": {
    "columns": [
      "day",
      "mnth",
      "year",
      "season",
      "holiday",
      "weekday",
      "workingday",
      "weathersit",
      "temp",
      "atemp",
      "hum",
      "windspeed"
    ],
    "index": [0],
    "data": [[1,1,2022,2,0,1,1,2,0.3,0.3,0.3,0.3]]
  }
}
```

Este JSON contém valores de entrada para cada coluna esperada pelo modelo. Envie a requisição POST para o endpoint da API com este JSON para ver a previsão gerada pelo modelo.

### Conclusão

Neste laboratório, aprendemos como configurar um ambiente de aprendizado de máquina no Azure, importar e preparar dados, treinar e avaliar um modelo e, finalmente, implantar e testar o modelo. Esta prática demonstra o poder do Azure Machine Learning e como ele pode facilitar o desenvolvimento de soluções de IA.

--- 

Este `README.md` cobre todos os passos, incluindo a configuração do ambiente, preparação e treinamento do modelo, e como realizar testes com o JSON de entrada fornecido.
