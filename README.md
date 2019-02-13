# OpenCollarAPI

Specifications and documentation for a universal standard API to access GPS collar data. 

Files: 
  + __README.md__ _The document you are currently reading_
  + __OpenCollarAPI.yaml__ _Specifies the API calls and responses according to the [OpenAPI 3.0](https://github.com/OAI/OpenAPI-Specification) standard_
  + __CSV.md__ _Information about how the csv requirements in this specificaiton_
  + __csvFormat.json__ _Specifies the formatting options for the CSV according to [CSV Dialect](https://frictionlessdata.io/specs/csv-dialect/)_

The main document in this project is the OpenCollarAPI yaml file. The preferred way to view the documentation is to [view the specification on with ReDoc](http://rebilly.github.io/ReDoc/?url=https://raw.githubusercontent.com/rgzn/OpenCollarAPI/master/OpenCollarAPI.yaml)

To use the SwaggerHub interface to view this API go here:
https://app.swaggerhub.com/apis/Open-Collar-Standard/open-collar_api/0.1.0

To edit the API yourself, I recommend pasting the yaml text into the swagger editor here:
https://editor.swagger.io

## About the OpenAPI standard ##

OpenAPI is the most popular standard for API documentation, specification, and generation. OpenAPI provides a format for precisely specifying all inputs and outputs of a http/s API. An API is specified using a yaml-formatted text file. From this text file, automated tools can generate the API servers, clients, and documentation. 


## About the OpenCollar API ##
This specification details the web requests and responses for a universal API for GPS tag data access. It specifies exactly the web requests and responses needed for clients to access the data generated by their GPS collars, tags, and associated devices. The API is designed around the data and functions common to all manufacturers, but is extendable to allow for individual manufacturers to add their own unique functions when needed. 

## Motivating Principles ##
This API is based on funamentals settled upon by talking to major GPS collar users such as state agencies and university researchers. Large scale GPS tag users often use multiple brands of collars. These clients have their own databases and analyses that combine data from many vendors. Ideally, these users are able to access data from each collar manufacturer using identical techniques. The interface does not need to be highly featured, it just needs to provide simple, reliable access to all the data that the tags upload to their servers. Most users want to access their data using automatically scheduled routines, so the interface must be able to handle that. 

## Key Features ##
In accordance with the above principles, this standard requires some features that may be new for data providers:
  + Each data record must include an upload timestamp. This is defined as a timestamp that identifies the moment when that record was made available on the server and became accessible to the user. 
  + All timestamped records have a request to search them by either the record timestamp or the upload timestamp. For the data client, this allows regularly scheduled downloads to capture all data without repetition, even when data is delayed in uploading. 
  + Each device that records data has a unique identifier string. Requests for data that specify which device to retrieve data from use this string as a query parameter. 

## What is specified by this standard? ##
Essentially every aspect of the interface between client and server is specified. 
This includes: 
  + Authentication process (multiple options provided)
  + Requests for information on GPS devices
  + Requests for data from GPS devices
  + Input parameters and data for all requests
  + Output response content and type

## What is not specified by this standard? ##
This standard specifies essentially nothing about the implementation details of the interface. 
Things *NOT* specified include:
  + Server software
  + Serverside database 
  + Client software
  + Additional functions. More paths may be added than are specified here. This standard just specifies a minimum set. 
