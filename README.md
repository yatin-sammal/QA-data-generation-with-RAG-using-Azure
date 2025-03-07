# Generating QA Dataset with RAG using Azure

This project demonstrates how to generate a QA dataset with Retrieval-Augmented Generation (RAG) using Azure OpenAI services.

## Prerequisites

- An Azure account
- Azure CLI installed (Optional)
- Python 3.10 or later installed

## Setup Instructions

### Step 1: Create an Azure Resource Group

1. Sign in to the Azure portal at https://portal.azure.com 
2. From the Azure portal home page, select + Create a resource.
   ![image](https://github.com/user-attachments/assets/64e70f2e-f373-4334-bc33-18c1dcb1a7ff)
   
   OR

   Open a terminal or command prompt and run the following command to create a new resource group:
    ```sh
    az group create --name myResourceGroup --location eastus
    ```
### Step 2: Create an Azure Machine Learning workspace

1. On the Create a resource page, use the search bar to find Azure Machine Learning and create Azure Machine Learning.
   ![image](https://github.com/user-attachments/assets/8ee3ae76-332d-424c-b0d3-463b95f083e1)

2. Provide the following information to configure your new workspace:
   1. Subscription: Select your assigned Azure subscription
   2. Resource group: Select Click New and give the name for eg: RGForMLOps
   3. Workspace name: enter alphanumeric characters for eg: Azuremlws2025
   4. Region: Select your nearest region (North Central US is selected here)
   5. Container registry: Select Create new. Enter alphanumeric characters for eg: azuremlcr2025
   ![image](https://github.com/user-attachments/assets/43444a94-0fa2-46cb-9824-1c0e1a5f78a8)

3. Once you are done configuring the workspace, select Review + Create.
   ![image](https://github.com/user-attachments/assets/f0775615-8d5a-4e2a-bb6b-276cba120968)

4. Once the Validation is passed, click on Create.
   ![image](https://github.com/user-attachments/assets/f8fc5a23-8836-4fd6-9911-c264d8ff9acc)

5. Once deployed click on go to resourse. On the overview page select Launch studio under Work with your model in Azure Machine Learning studio.
   ![image](https://github.com/user-attachments/assets/2130f4e5-c690-47c1-9335-54f10982b00d)



### Step 3: Set Up Azure OpenAI Services

1. Search for and select Azure OpenAI. Create an Azure OpenAI service:
   ![image](https://github.com/user-attachments/assets/df367184-d109-4b3b-b990-df3e44ead274)

2. Fill in the below details and click on Next:
   1. Resource group - Select the resourse group created in Step 1 for eg: RGForMLOps
   2. Region – Select any nearest region (East US2 is being used here)
   3. Name - Enter alphanumeric characters for eg: AOAI-PF2025
   4. Pricing tier - Standard
      ![image](https://github.com/user-attachments/assets/fc3ecfad-d6db-465b-b720-8818e438f55c)

3. Accept the defaults in the next pages and click on Create in the Review + create page.
   ![image](https://github.com/user-attachments/assets/c07392c2-ffb9-4367-b774-19e3db1a92be)

4. Click on Go to resource once the deployment is complete and Select Keys and Endpoint under Resource Management from the left pane.
5. Copy the API key and the endpoint for the Azure OpenAI service.
   ![image](https://github.com/user-attachments/assets/0ff9af5b-cf3f-4d3c-a9c3-67392f7c4617)


### Step 4: Model selection and prompt flow connection setup

1. Naviagte to Azure Machine Learning Studio Page and select Model catalog from the left pane.
2. Search for gpt-35-turbo and select gpt-35-turbo-16k from the models list.
   ![image](https://github.com/user-attachments/assets/0adb9cf2-7280-4c2c-9bce-739d3de031ce)
   
3. Ensure that the AOAI resource is selected in the Azure OpenAI resource field. Select Deploy to deploy the model.
   ![image](https://github.com/user-attachments/assets/7a6013c7-d7f2-4557-9867-d0c1f9b62594)

4. Accept the Deployment name and select Deploy.
   ![image](https://github.com/user-attachments/assets/bd4916fe-539e-439f-a9ba-3c76f86d22ba)

5. Repeat the model deployment for text-embedding-ada-002 with the deployment name as text-embedding-ada-002-2

### Step 5: Set up the environment

1. From the left pane of the Studio, select Notebooks. Click on the three dots next to the user name and select Upload files.
   ![image](https://github.com/user-attachments/assets/83a6b64f-a3c2-47c6-8072-c1a25572fe98)

2. Browse and select the qa_data_generation.ipynb file. Select I trust contents of this file checkbox and click on Upload.
   ![image](https://github.com/user-attachments/assets/ae0fe031-a53a-413e-b287-b5d5bf5eb5b9)

3. Open the notebook and select Serverless Spark Compute in the Compute option.
   ![image](https://github.com/user-attachments/assets/f31fc290-5777-4a33-a043-a0151b1ff0f1)

4. Once the compute is attached, select Configure session to upload the conda.yml file and set up the environment for execution using it.
   ![image](https://github.com/user-attachments/assets/97e30ba5-ca25-41b1-8ed7-154e04544ca2)

5. Select Python packages ->Upload Conda file -> click on Browse. Upload the conda.yml and select Apply.
   ![image](https://github.com/user-attachments/assets/95f13555-e380-471a-8488-7ca899c04b3e)

6. Execute the first cell of the notebook to install the dependencies. Follow the next steps mentioned in the notebook to continue
Note: The first cell will take 10 to 15 minutes to complete. If the session does not come to Ready state after 15 minutes, refresh the page and then execute the first cell.

## Final Output
Upon successful execution of the notebook, you will have a QA dataset generated using the RAG approach with Azure OpenAI services. This dataset can be used for various natural language processing tasks, such as training QA models or evaluating the performance of existing models.

Azure show the execution in a prompt flow where you can explore each stage of the flow.
![image](https://github.com/user-attachments/assets/ffc54719-23bc-4bf7-8359-7b72befa09f6)
![image](https://github.com/user-attachments/assets/4f186b55-0f18-40ec-aa08-8596c6cfde60)

   
## Additional Resources

- [Azure OpenAI Service Documentation](https://docs.microsoft.com/en-us/azure/cognitive-services/openai/)
- [Azure CLI Documentation](https://docs.microsoft.com/en-us/cli/azure/)
