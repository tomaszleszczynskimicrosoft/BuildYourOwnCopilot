# Deployment - Standard

## Prerequisites

- Azure Subscription
- Subscription access to Azure OpenAI service. Start here to [Request Access to Azure OpenAI Service](https://aka.ms/oaiapply)
- .NET 8 SDK
- Docker Desktop
- Azure CLI ([v2.51.0 or greater](https://docs.microsoft.com/cli/azure/install-azure-cli))
- [Helm 3.11.1 or greater](https://helm.sh/docs/intro/install/) (for AKS deployment)
- Visual Studio 2022 (only needed if you plan to run/debug the solution locally)

>**NOTE**: Installation requires the choice of an Azure Region. Make sure to set region you select which is used in the `<location>` value below supports Azure OpenAI services.  See [Azure OpenAI service regions](https://azure.microsoft.com/explore/global-infrastructure/products-by-region/?products=cognitive-services&regions=all) for more information.

## Deployment steps

Follow the steps below to deploy the solution to your Azure subscription.

1. Ensure all the prerequisites are installed.  

2. Clone the repository:
   
    ```cmd
    git clone https://github.com/Azure/BuildYourOwnCopilot.git
    ```

3. Switch to the `main` branch:

    ```cmd
    cd BuildYourOwnCopilot
    git checkout main
    ```

4. Run the following script to provision the infrastructure and deploy the API and frontend. This will provision all of the required infrastructure, deploy the API and web app services into your choice of Azure Kubeternetes Service or Azure Container Apps, and import data into Azure Cosmos DB.

    ### Deploy with Azure Kubernetes Service
    This script will deploy all services including a new Azure OpenAI account and AKS

    ```pwsh
    cd ./infra/aks
    azd up
    ```

    You will be prompted for the target subscription, location, and desired environment name.  The target resource group will be `rg-` followed by the environment name (i.e. `rg-my-aks-deploy`)

### Deploy with Azure Container Apps
    This script will deploy all services including a new Azure OpenAI account using Azure Container Apps. (This can be a good option for users not familiar with AKS)

    ```pwsh
    cd ./infra/aca
    azd up
    ```

    You will be prompted for the target subscription, location, and desired environment name.  The target resource group will be `rg-` followed by the environment name (i.e. `rg-my-aca-deploy`)
