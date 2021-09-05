# demo-azure-web-app-deployment
 
## Create an Azure website using the Azure CLI & Deploy Code from GitHub

```powershell
export RESOURCE_GROUP=learn-4e18e730-c221-430b-bc4e-6feac0b20082
export AZURE_REGION=centralus
export AZURE_APP_PLAN=popupappplan-$RANDOM
export AZURE_WEB_APP=popupwebapp-$RANDOM

# Create app service plan
az appservice plan create --name $AZURE_APP_PLAN --resource-group $RESOURCE_GROUP --location $AZURE_REGION --sku FREE

# Create Web App
az webapp create --name $AZURE_WEB_APP --resource-group $RESOURCE_GROUP --plan $AZURE_APP_PLAN

# Access Web app  
curl $AZURE_WEB_APP.azurewebsites.net

# Deploy this SPA Source Code from GitHub to your Azure Web App
az webapp deployment source config --name $AZURE_WEB_APP --resource-group $RESOURCE_GROUP --repo-url "https://github.com/rupeshtiwari/demo-azure-web-app-deployment" --branch main --manual-integration --git-token "your github token" --debug

# Access site again 
curl $AZURE_WEB_APP.azurewebsites.net
```

![](https://i.imgur.com/9N8FPSZ.png)
