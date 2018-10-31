
# CaptureOrder

[![Build Status](https://dev.azure.com/theazurechallenge/Kubernetes/_apis/build/status/Code/Azure.azch-captureorder)](https://dev.azure.com/theazurechallenge/Kubernetes/_build/latest?definitionId=10)

A containerised Go swagger API to capture orders, write them to MongoDb and an AMQP message queue.



## Usage
### Swagger

Access the Swagger UI at [http://[host]/swagger]()

### Submitting an order

```
POST /v1/Order HTTP/1.1
Host: [host]:[port]
Content-Type: application/json

{
  "EmailAddress": "test@domain.com",
  "PreferredLanguage": "en"
}
```

## Environment Variables

The following environment variables need to be passed to the container:

### Logging

```
ENV TEAMNAME=[YourTeamName]
ENV APPINSIGHTS_KEY=[YourCustomApplicationInsightsKey] # Optional, create your own App Insights resource
```

### For MongoDB

```
ENV MONGOURL=mongodb://[mongoinstance].[namespace]
```

### For CosmosDB

```
ENV MONGOURL=mongodb://[CosmosDBInstanceName]:[CosmosDBPrimaryPassword]=@[CosmosDBInstanceName].documents.azure.com:10255/?ssl=true&replicaSet=globaldb
```

### For RabbitMQ

```
ENV AMQPURL=amqp://[url]:5672
```

### For Event Hubs

```
ENV AMQPURL=amqps://[policy name]:[policy key]@[youreventhub].servicebus.windows.net/[eventhubname]
```

Make sure your _policy key_ is URL Encoded. Use a tool like: <https://www.url-encode-decode.com/>

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
