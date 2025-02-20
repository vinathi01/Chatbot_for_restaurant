# Chatbot_for_restaurant
# Overview
The Interactive Restaurant Chatbot is an intelligent Natural Language Processing (NLP) chatbot designed to streamline restaurant ordering systems. Built using **Dialogflow**, **Python (FastAPI)**, and **MySQL**, this chatbot facilitates both customer interactions through a web interface and backend operations for managing orders, intents, and entities.

This project enhances the restaurant ordering experience by automating order placements, answering common customer inquiries, and ensuring seamless integration with the backend database. This README provides comprehensive instructions on setting up and running the project.
# Directory Structure

The project is structured as follows:

    ├── backend/           # Contains the Python FastAPI backend code
    ├── db/                # Database dump (import into MySQL database using MySQL Workbench)
    ├── dialogflow_assets/ # Training phrases, intents, and entities for Dialogflow
    ├── frontend/          # Website code

# Installation Instructions

## 1. Install Required Python Modules
   
You can install the necessary dependencies using either of the following methods:

### Option 1: Install modules individually

Run the following commands:

    pip install mysql-connector
    pip install "fastapi[all]"

### Option 2: Install all dependencies using a requirements file

Run the following command to install all required modules:

    pip install -r backend/requirements.txt

## 2. Database Setup
   
### Import Database Dump into MySQL

  1.  Open MySQL Workbench or any MySQL client.
  
  2.  Create a new database (if not already created).
  
  3.  Import the database dump located in the db/ folder into MySQL:
  
   - In MySQL Workbench: Navigate to Server > Data Import, select the dump file, and import.

   - Using MySQL CLI:
   ```bash
      mysql -u your_username -p your_database_name < db/database_dump.sql
  ```
     
  4.  Ensure the database credentials match those in the backend code.

## 3. Starting the FastAPI Backend Server
### Navigate to the Backend Directory
    cd backend
### Start the FastAPI Server
    uvicorn main:app --reload
    
  Upon successful execution, the server will be accessible at:

    http://127.0.0.1:8000

## 4.Setting Up HTTPS Tunneling with Ngrok
To enable external access to the FastAPI server and integrate it with Dialogflow, set up an HTTPS tunnel using Ngrok.
### Steps to Set Up Ngrok:
1.  Download and Install Ngrok:
  - Visit Ngrok's official website and download the version compatible with your OS.
  - Extract the downloaded file.
    
2.  Run Ngrok:
  - Open a terminal or command prompt.
  - Navigate to the folder containing the Ngrok executable.
  - Run the following command:
    ```
    ngrok http 8000
    ```
3.  Obtain the Public HTTPS URL:

  - Once Ngrok is running, it will generate a public HTTPS URL (e.g.,https://randomstring.ngrok.io).

  - Use this URL as the webhook URL in your Dialogflow project settings.

## Important Notes:
  - Ngrok sessions may expire after some time. If you encounter a timeout or expiration message, restart the Ngrok session.

  - Ensure that your Dialogflow webhook configuration is updated with the new URL whenever the Ngrok session is restarted.
    
  - Ensure that your backend code is properly configured with database credentials and environment-specific settings.

  - If you modify the FastAPI backend or Dialogflow configuration, restart the server to apply changes.

  - System logs are available in the backend directory. Monitor them for debugging any errors.

## 5.  Configuring Dialogflow
  - To integrate the chatbot with Dialogflow, follow these steps:

  - Navigate to the Dialogflow Console (Dialogflow Console).

  - Create a new agent or select an existing agent.

  - Navigate to Fulfillment and enable Webhook.

  - Set the webhook URL to the Ngrok-generated URL.

  - Navigate to Intents and define the necessary training phrases and responses.

  - Upload the dialogflow_assets/ directory contents (including intents and entities) to your Dialogflow agent.

## 6. Frontend Setup

To run the web-based customer interface:

Navigate to the frontend directory:

    ```
    cd frontend
    ```
Open the index.html file in a browser or serve it using a local server:
```
python -m http.server 8080
```
The website will be accessible at:
```
http://127.0.0.1:8080
```



