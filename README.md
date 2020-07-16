# Petronas Data Academy - Azure Data Platform

In this workshop you will learn about the main concepts related to advanced analytics and Big Data processing and how Azure Data Services can be used to implement a modern data warehouse architecture. You will learn what Azure services you can leverage to establish a solid data platform to quickly ingest, process and visualise data from a large variety of data sources. The reference architecture you will build as part of this exercise has been proven to give you the flexibility and scalability to grow and handle large volumes of data and keep an optimal level of performance.

In the exercises in this lab you will build data pipelines using data related to New York City. The workshop was designed to progressively implement an extended modern data platform architecture starting from a traditional relational data pipeline. Then we introduce big data scenarios with large data files and distributed computing. We add non-structured data and AI into the mix and finish off with real-time stream analytics. You will have done all of that by the end of the workshop.

**IMPORTANT**:

* The reference architecture proposed in this workshop aims to explain just enough of the role of each of the Azure Data Services included in the overall modern data platform architecture. This workshop does not replace the need of in-depth training on each Azure service covered.

* The services covered in this course are only a subset of a much larger family of Azure services. Similar outcomes can be achieved by leveraging other services and/or features not covered by this workshop. Specific business requirements may require the use of different services or features not included in this workshop.

* Some concepts presented in this course can be quite complex and you may need to seek more information from different sources to compliment your understanding of the Azure services covered.

![](./Media/ModernDataPlatformReferenceArchitecture.jpg)

## Document Structure
This document contains detailed step-by-step instructions on how to implement a Modern Data Platform architecture using Azure Data Services. It’s recommended you carefully read the detailed description contained in this document for a successful experience with all Azure services. 

You will see the label **IMPORTANT** whenever a there is a critical step to the lab. Please pay close attention to the instructions given.

You will also see the label **IMPORTANT** at the beginning of each lab section. As some instructions need to be executed on your host computer while others need to be executed in a remote desktop connection (RDP), this **IMPORTANT** label states where you should execute the lab section. See example below:

**IMPORTANT**|
-------------|
**Execute these steps on your host computer**|

## Data Source References
New York City data used in this lab was obtained from the [New York City Open Data website](https://opendata.cityofnewyork.us/). The following datasets were used:
    <br>- [NYPD Motor Vehicle Collisions](https://data.cityofnewyork.us/Public-Safety/NYPD-Motor-Vehicle-Collisions/h9gi-nx95)
    <br>- [TLC Yellow Taxi Trip Data](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

## Lab Prerequisites and Deployment
The following prerequisites must be completed before you start these labs:

* You must be connected to the internet;

* Use either Edge or Chrome when executing the labs. Internet Explorer may have issues when rendering the UI for specific Azure services.

* You must have a Pay-As-You-Go Azure account with administrator- or contributor-level access to your subscription. If you don’t have an account, you can sign up for an account following the instructions here: [link](https://azure.microsoft.com/en-au/pricing/purchase-options/pay-as-you-go/). 

    <br>**IMPORTANT**: Azure free subscriptions have quota restrictions that prevent the workshop resources from being deployed successfully. Please use a Pay-As-You-Go subscription instead.

    <br>**IMPORTANT**: When you deploy the lab resources in your own subscription you are responsible for the charges related to the use of the services provisioned. For more information about the list of services and tips on how to save money when executing these labs, please visit the Cost Management section of the [Lab 0: Deploy Azure Data Platform End2End to your subscription](./Deploy/Deploy.md) page.

* Labs 1 to 2 require you to open a Remote Desktop Connection (RDP) to Azure Virtual Machines. If you are using a Mac, please ensure you have the latest version of the Microsoft Remote Desktop software installed: [link] (https://apps.apple.com/us/app/microsoft-remote-desktop-10/id1295203466?mt=12)

* Lab 4 requires you to have a Power BI Pro account. If you don’t have an account you can sign up for a 60-day trial for free here: [link](https://powerbi.microsoft.com/en-us/power-bi-pro/)
  
## Lab Guide

Throughout a series of 4 labs you will progressively implement a modern data platform architecture using datasets from New York City. 

You will start ingesting relational data about motorvehicle collisions in Manhattan hosted in an Azure SQL Database into your Azure Synapse Analytics data warehouse. Then we will introduce the concepts of data lake and  big data challenges and you will put these into practice by ingesting and processing over 50 million yellow taxi ride records stored as large data files stored in your data lake.

You will then use Databricks and the power of Spark clusters to explore big data files. Then finally, you will use a LogicApp to simulate high-frequency stock purchase transactions as a source of streaming events that you will capture, store and process in real time with Event Hubs, Stream Analytics and Power BI.

### [Lab 0: Deploy Azure Data Platform End2End to your subscription](./Deploy/Deploy.md)

**IMPORTANT**: You should skip this Lab if you are executing the labs through subscriptions provided by CloudLabs. All Azure services will be deployed as you activate your registration.

In this section you will automatically provision all Azure resources required to complete labs 1 through to 4. We will use a pre-defined ARM template with the definition of all Azure services used to ingest, store, process and visualise data. 

The estimated time to complete this lab is: **30 minutes**.

**IMPORTANT**|
-------------|
**In order to avoid potential delays caused by issues found during the ARM template deployment it is recommended you execute Lab 0 prior to Day 1.**|

### [Lab 1: Load Data into Azure Synapse Analytics using Azure Data Factory Pipelines](./Lab/Lab1/Lab1.md)

In this lab you will configure the Azure environment to allow relational data to be transferred from an Azure SQL Database to an Azure Synapse Analytics database using Azure Data Factory. The dataset you will use contains data about motor vehicle collisions that happened in New York City from 2012 to 2019. You will use Power BI to visualise collision data loaded from Azure Synapse Analytics.

The estimated time to complete this lab is: **45 minutes**.

Step     | Description
-------- | -----
![1](./Media/Black1.png) | Build an Azure Data Factory Pipeline to copy data from an Azure SQL Database table
![2](./Media/Black2.png) | Use Azure Data Lake Storage Gen2 as a staging area for Polybase
![3](./Media/Black3.png) | Load data to an Azure Synapse Analytics table using Polybase
![4](./Media/Black4.png) | Visualize data from Azure Synapse Analytics using Power BI

![](./Lab/Lab1/Media/Lab1-Image51.png)

### [Lab 2: Transform Big Data using Azure Data Factory Mapping Data Flows](./Lab/Lab2/Lab2.md)
In this lab you will use Azure Data Factory to download large data files into your data lake and use an Azure Synapse Analytics stored procedure to generate a summary dataset and store it in the final table. The dataset you will use contains detailed New York City Yellow Taxi rides for the first half of 2019. You will generate a daily aggregated summary of all rides using Mapping Data Flows and save the resulting dataset into your Azure Synapse Analytics data warehouse. You will then use Power BI to visualise summarised data. 

The estimated time to complete this lab is: **60 minutes**.

 
Step     | Description
-------- | -----
![](./Media/Green1.png) | Build an Azure Data Factory Pipeline to copy big data files from shared Azure Storage
![](./Media/Green2.png) | Ingest data files into your data lake
![](./Media/Green3.png) | Use Mapping Data Flows to generate a aggregated daily summary and save the resulting dataset into your Azure Synapse Analytics data warehouse.
![](./Media/Green4.png) | Visualize data from your Azure Synapse Analytics using Power BI

![](./Lab/Lab2/Media/Lab2-Image40.png)

### [Lab 3: Explore Big Data using Azure Databricks](./Lab/Lab3/Lab3.md)
In this lab you will use Azure Databricks to explore the New York Taxi data files you saved in your data lake in Lab 2. Using a Databricks notebook you will connect to the data lake and query taxi ride details. 

The estimated time to complete this lab is: **45 minutes**.

Step     | Description
-------- | -----
![](./Media/Red1.png) |Build an Azure Databricks notebook to explore the data files you saved in your data lake in the previous exercise. You will use Python and SQL commands to open a connection to your data lake and query data from data files.
![](./Media/Red2.png) |Integrate datasets from Azure Synapse Analytics data warehouse to your big data processing pipeline. Databricks becomes the bridge between your relational and non-relational data stores.

![](./Lab/Lab3/Media/Lab3-Image14.png)

### [Lab 4: Ingest and Analyse real-time data with Event Hubs and Stream Analytics](./Lab/Lab4/Lab4.md)
In this lab you will use an Azure Logic App to simulate a NYSE stream of stock purchase transactions. The logic app will then send the messages to Event Hubs. You will then use Stream Analytics to receive and process the stream and perform aggregations to calculate the number of transactions and amount traded in the last 10 seconds. Stream Analytics will send the results to a real-time dataset in Power BI.

The estimated time to complete this lab is: **45 minutes**.

Step     | Description
-------- | -----
![](./Media/Orange1.png) | Review the Azure Logic App logic that simmulates the NYSE transaction stream sent to EventHubs
![](./Media/Orange2.png) | Save simulated NYSE stock transaction messages into your data lake for future analysis (cold path)
![](./Media/Orange3.png) | Send stream of NYSE stock transaction messages to Stream Analytics for real-time analytics (hot path)
![](./Media/Orange4.png) | Incorporate Stock Company reference data into your stream processing logic
![](./Media/Orange5.png) | Visualize real-time data generated by Stream Analytics with Power BI

![](./Lab/Lab5/Media/Lab4-Image66.png)
