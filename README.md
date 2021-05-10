# CloudIoTRaspberry
Using Cloud IoT to stream Heart rate data Using Raspberry Pie
Cloud Internet of Things IoT Core is a fully managed service to connect, manage, and ingest data from globally dispersed devices easily and securely. Cloud IoT Core, in combination with other services on Cloud IoT platform, provides a complete solution for collecting, processing, analyzing, and visualizing IoT data in real time to support improved operational efficiency. Google Cloud's IoT Core addresses simplifies these tasks which makes it easier to focus on gaining value and insight from an IoT project.
In this lab, A Raspberry Pi with a heart rate sensor will be used for the IoT device and several components of the Google Cloud Platform will form the data pipeline. We will build a data pipeline that starts with an Internet of Things (IoT) device that captures heart rate, leverages IoT Core to securely publish the data to a message queue where it will then be transported into a data warehouse. 
![image](https://user-images.githubusercontent.com/81333410/117591581-bfbbca80-b0fa-11eb-8472-041650c7669f.png)

 
After completing the steps in this lab, you will have a streaming data pipeline feeding a data warehouse where it can be retrieved to graphically display heart rate data over time.
 

Requirements:
•	A Google Cloud Platform account. 
•	To build the IoT sensor portion of this lab instead of leveraging sample data and a script, we will also need the following 
o	Raspberry Pi with power supply, SD memory card and case, USB card reader, Female-to-male breadboard wires, Polar T34 Heart Rate Transmitter and Polar Heart Rate receiver. In addition, we should have access to a computer monitor or TV with HDMI input, HDMI cable, keyboard and a mouse is assumed.
Steps to Setup Google cloud IoT
1.	Sign-in to Google Cloud Platform console ( console.cloud.google.com).
2.	Create a new project with name ‘iot-heartrate’.
 
3.	Enable APIs and Services - Search for PubSub. Click on the results that says "Cloud Pub/Sub API" and, on the following page, "Enable API".
 
 
4.	Create a BigQuery table - BigQuery is a serverless, highly scalable, low cost enterprise data warehouse. From the Cloud Console, select BigQuery and then Create new dataset – “heartRateData"
    
5.	Create a Pub/Sub topic and subscription - Cloud Pub/Sub is a simple, reliable, scalable foundation for streaming data and event-driven computing systems. As a result, it is perfect for handling incoming IoT messages and then allowing downstream systems to process them which is why it is tightly linked with Cloud IoT Core. Enter "heartratedata" as the topic name and then click Create
 
Enter "heartratedata" as the subscription name, leave the delivery type as "Pull" and then click Create
       

6.	Use a Dataflow Template - Dataflow will need a location to store temporary files, so we will provide a location in Google Cloud Storage. From the Cloud Console, select Storage and then Browser. First create a Bucket
 
From the Cloud Console, select Dataflow. Click on Create Job from Template. Give the job a name and select the Pub/Sub Subscription to Big/Query template. Click on Run Job.
 
7.	Run the Job - Your connection is cone successfully in between Pub/Sub to BigQuery via Dataflow.
                
8.	Create an IoT Core registry.
 
9.	Add the device to the IoT Core Registry
 
10.	IoT Core is now ready to receive communication from the Raspberry Pi.
 
11.	Start the data by using following steps on the terminal/cmd prompt.
 


12.	Check to make sure that data is flowing into the BigQuery table. If data is flowing properly then we will see the results when execute the select query on the table. 
         
13.	Visualize the data using Google Sheets as shown below.
 


Summary:
This report shows the procedure to use Google cloud IoT to recore the data from Raspberry pie. The Steps explains in detail how to create Google Pub/Sub, data pipeline, Google Cloud Dataflow template, Repository, device, Topic, subscription, and leverage Google BigQuery. The output above shows that we have created an entire data pipeline.  We have used Google IoT Core to secure IoT devices and to allow data to flow into Google Pub/Sub, deployed Dataflow from a template and pushed data into BigQuery and then used the integration with Google Sheets to perform a quick data visualization on the data received in table. We can create various visualizations on the data and represent our data
