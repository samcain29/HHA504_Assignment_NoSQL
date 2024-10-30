# HHA504 Assignment: Working with Managed NoSQL Databases

## Objective
The goal of this assignment was to gain hands-on experience with managed NoSQL database services on Azure and Google Cloud Platform (GCP), specifically Google BigQuery, MongoDB Atlas, and Redis Cloud. Using a healthcare dataset, we uploaded, queried, and manipulated data across these services.

---

## Dataset
Dataset used: [Healthcare Dataset CSV](https://raw.githubusercontent.com/hantswilliams/HHA-504-2024/refs/heads/main/other/module8/module8_nosql_hw.csv)

---

## Step 1: Start and Configure Databases

### A. Google BigQuery Setup

1. **Dataset Creation**:
   - Accessed BigQuery via the Google Cloud Console.
   - Created a new dataset named `nosql_healthcare` in my project.

2. **CSV Upload**:
   - Uploaded the healthcare dataset as a table in BigQuery.
   - Configured the schema with appropriate data types.

3. **Connection Details**:
   - Project ID: cain-samantha-hha504
   - Dataset ID: nosql_healthcare
   - Table ID: patients
     
**Screenshot of BigQuery Dataset and Table Setup**  
  ![image](https://github.com/user-attachments/assets/d3956b59-96c9-47b9-824e-41af7af32578)


---

### B. MongoDB Atlas Setup

1. **Account Creation and Cluster Setup**:
   - Signed up for MongoDB Atlas using my Stony Brook email and created a free-tier cluster.
   - Created a new database and collection named `Cluster0`.
  ![image](https://github.com/user-attachments/assets/6264bd89-dcf6-4ba6-a30b-81929994d459)

2. **Data Conversion and Insertion**:
   - Converted the CSV file to JSON format using Python in Google  Colab:
  ![image](https://github.com/user-attachments/assets/a7ed1b97-f79c-4c6e-8b75-e6041fcadcea)

   - Inserted the JSON data into MongoDB using pymongo:
  ![image](https://github.com/user-attachments/assets/09b0abbe-a5a1-4ea1-8106-7bac7975b3b0)

3. **Connection Details**:
   - MongoDB connection string for Compass: mongodb+srv://samanthacain:thumbles29>@cluster0.vwka3.mongodb.net/

**Screenshot of MongoDB Atlas Cluster and Collection**  
  ![image](https://github.com/user-attachments/assets/65a56479-0180-434c-a2ba-051862c851dd)


---

### C. Redis Cloud Setup

1. **Account Creation and Database Setup**:
   - Signed up for Redis Cloud using my Stony Brook email and connected to the StonyBrookMedicine-free-db.
    ![image](https://github.com/user-attachments/assets/46a8a75a-dcec-46cc-ad18-e5d417d3fcd5)


2. **Data Insertion**:
   - Used the PatientID as the key and inserted each patient record as the value, serialized to JSON using Google Colab.
    ![image](https://github.com/user-attachments/assets/8aa8c016-f34a-4b42-8519-32af5a630d1c)

   - Downloaded Redis Insight and opened database within the app


4. **Connection Details**:
   - Host: redis-17380.c1.us-central1-2.gce.redns.redis-cloud.com
   - Port: 17380
   - Password: aSSdmifp0gQQnr2QT37hBYPv0Fn632D2

**Screenshot of Redis Cloud Database Setup**  
  ![image](https://github.com/user-attachments/assets/ee4943b3-b363-424d-bcc7-5693009d2ac0)

---

## Step 2: Explore BigQuery (GCP)

1. **SQL Query Execution**:
   - In BigQuery’s Query Editor, I ran the following SQL query to retrieve patients older than 40:
     ```sql
     SELECT *
     FROM `cain-samantha-hha504.nosql_healthcare.patients`
     WHERE Age > 40;
     ```

2. **Monitoring Usage and Cost**:
   - Observed query cost and job details through the Query Job Details pane.

**Screenshot of BigQuery Query Results**  
  ![image](https://github.com/user-attachments/assets/1403f79e-09b8-41a2-8d1e-bb13675aebeb)


---

## Step 3: Modify and Explore Data in MongoDB Atlas and Redis Cloud

### A. MongoDB Atlas Queries

1. **Data Retrieval**:
   - Used the MongoDB Atlas Query Builder to find all patients older than 40.
   ![image](https://github.com/user-attachments/assets/860fd023-a726-4f16-9b95-d28322049bca)

### B. Redis Cloud Data Manipulation

1. **Data Retrieval**
   - Retrieved data for PatientID = 1
     ![image](https://github.com/user-attachments/assets/90d27d09-ff6b-43c5-8561-65bc1bcd6097)
     
2. **Data Update**
   - Updated the TreatmentPlan for PatientID = 1
     ![image](https://github.com/user-attachments/assets/b26c68fe-267f-464e-9565-2cb29f7bfc39)

---

## Step 4: Describe Your Experience

### BigQuery
- **Setup**: BigQuery was straightforward for uploading and querying structured data. The Query Editor and job details made it easy to run queries and monitor costs.
- **Usability**: I found the interface easy to navigate, and running SQL queries felt intuitive. BigQuery's pay-as-you-go model was convenient for ad hoc analysis.

### MongoDB Atlas
- **Setup**: Setting up a cluster and inserting data was a smooth process, though converting data to JSON required additional steps.
- **Usability**: MongoDB Atlas’s Query Builder was user-friendly, allowing me to execute queries and view results quickly. However, managing NoSQL documents required a bit more adjustment compared to relational databases.

### Redis Cloud
- **Setup**: Setting up Redis Cloud was simple, but managing data as key-value pairs was different from traditional databases.
- **Usability**: Redis performed well for simple key-value operations, but querying specific fields required extra effort. Redis’s speed and efficiency in retrieving and updating individual records made it ideal for real-time data access.
