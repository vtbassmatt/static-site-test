# Testing out publishing to an Azure static site

The contents of the `html/` directory are published to https://ohgn28lr3q.z21.web.core.windows.net/ by an Azure Pipeline.

Steps required:
1. Set up an Azure Storage account
2. Enable the "static website (preview)" feature
3. Copy the connection string from the Azure portal into a secret variable on the pipeline.
4. Map in that secret as "AZURE_STORAGE_CONNECTION_STRING" in the environment.
5. Run these commands:
```yaml
    az extension add --name storage-preview
    az storage blob upload-batch -s $SOURCE_PATH -d '$web'
```
