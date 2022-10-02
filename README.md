# Java Functions examples for Google Cloud (previously called GCP) Functions.

This repository offers functionalities interacting in different ways for Google Cloud Functions.

# Functionalities you can use.
The Google Cloud provides some different ways to execute code as a function. This repository focuses on the 2 ways below.

- HTTP trigger  
  After deploying your function with an HTTP trigger, it will have an endpoint URL where you can invoke your function.  
  [HTTP triggers | Cloud Functions Documentation | Google Cloud](https://cloud.google.com/functions/docs/calling/http)
  
- Pub/Sub trigger  
  You can connect a Pub/Sub topic with your function.
  When you publish a message to the Pub/Sub topic, then your funciton receives the message and performs your code.  
  [Pub/Sub triggers | Cloud Functions Documentation | Google Cloud](https://cloud.google.com/functions/docs/calling/pubsub)
  
This repository offers 2 different ways for each type of functions.

- HelloWorldHttpFunction  
  This class corresponds to the former trigger. A request data what its endpoint receives will be delivered to this function.

- HelloWorldSubscriberFunction  
  This class corresponds to the latter one. This function accepts a certain data structure what a Pub/Sub topic delivers.

# Usage
## Prerequisite
Complete all stuffs described in the "before you begin" and "Prerequisites" sections on the documents below.  
Particularly, you need a Pub/Sub topic in advance if you deploy a function with a Pub/Sub trigger.  

https://cloud.google.com/functions/docs/tutorials/http#before-you-begin
https://cloud.google.com/functions/docs/tutorials/pubsub#before-you-begin

## Deploy a Cloud Function with an HTTP trigger
At first, clone this repository on your local machine.  
Then go to the top level of the local repository.  

Executing the command below, you can deploy the sample code as a Function with an HTTP trigger.  
You can find detailed explanation of the options at [Deploy a Cloud Function](https://cloud.google.com/functions/docs/deploy).

```
$ gcloud functions deploy java-http-function-helloworld \
  --gen2 
  --runtime=java17
  --region=us-west1
  --source=.
  --entry-point=helloworld.HelloWorldHttpFunction
  --trigger-http
  --allow-unauthenticated
```

## Deploy a Cloud Function interacting with a Pub/Sub topic
At first, create a Pub/Sub topic. Let's assume you make a Pub/Sub topic named "helloworld".  
Then, clone this repository on your local machine and go to the top level of it.  

Executing the command below, you can deploy the sample code as a Function connected to a Pub/Sub topic.  
You can find detailed explanation of the options at [Deploy a Cloud Function](https://cloud.google.com/functions/docs/deploy).

```
$ gcloud functions deploy java-pubsub-function-helloworld \
  --gen2 \
  --runtime=java17 \
  --region=us-west1 \
  --source=. \
  --entry-point=helloworld.HelloWorldSubscriberFunction \
  --trigger-topic=helloworld
```

# References
[Cloud Functions overview](https://cloud.google.com/functions/docs/concepts/overview)  
[HTTP Tutorial (2nd gen)](https://cloud.google.com/functions/docs/tutorials/http)  
[Cloud Pub/Sub Tutorial (2nd gen)](https://cloud.google.com/functions/docs/tutorials/pubsub)  
[Write Cloud Functions](https://cloud.google.com/functions/docs/writing)  
[Deploy a Cloud Function](https://cloud.google.com/functions/docs/deploy)  

