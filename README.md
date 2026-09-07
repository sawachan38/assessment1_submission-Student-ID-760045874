# 1. Project Overview
Based on the medical data in the original four csv files, whose entities are; doctors, hospitals, patients and prescriptions, respectively, I created a new relational database by importing and processing the data using MySQL.
<br>The process involved organising csv data into separate tables for each entity, defining primary keys and foreign keys to establish relationships between entities, and creating an additional table that integrates information on patients and doctors.
<br>Once this process is completed, I then developed a set of SQL queries out of the new database I had created, to retrieve specific infomation required by the task, such as identifying the doctor who made the most prescription.
<br>Overall, this project demonstrates the use of data import, relational database modelling, and SQL queries to manage and extract meaningful infomration from the given dataset. 


# 2. Main Files
## 2-1. assessment1_database.sql
### 2-1-1. Overview
This .sql file contains SQL command lines to restore the database with four tables for each of the four entities (doctors, hospitals, patients, prescriptions) and one table (patients_to_doctors), which integrates data on patients and doctors table (as instructed in the task), all of which created by loading the original four csv files that I had cloned from the given link to a GitHub repository, and processing the data using my SQL.
### 2-1-2. Database Structure
* doctors stores personal information on doctors and their associated hospital.
* hospitals stores general information on hospitals.
* patients stores personal information on patients and their assigned doctor. 
* prescriptions stores general information on prescription for each patient made by their assigned doctor.
* patients_to_doctors stores personal information on patients and doctors, with each patient assigned to a single doctor.  

## 2-2. queries.sql
### 2-2-1. Overview
This .sql file includes a list of 6 command lines of SQL queries to retrieve certain information specified in the task. 
### 2-2-2. Query Descriptions
* The 1st query lists all doctors based at a particular hospital.
* The 2nd query lists all prescriptions for a particular patient, ordered by the prescription date.
* The 3rd query lists all prescriptions that a particular doctor has prescribed.
* The 4th query adds a new patient to the database, including being registered with one of the doctors.
* The 5th query identifies which doctor has made the most prescriptions.
* The 6th query lists all doctors at the hospital with biggest size (number of beds).

## 2-3. ERD.png
### 2-3-1. Overview
This png file contains a Entity Relationship Diagram of the 4 entities, showing the primary keys and foreign keys of each entity.

## 2-4. pseudocodes.md
This file contains pseudocodes which show how I broke down the task and planned how to organise the database identify relationships, and write SQL queries


# 3. How to use the files
## 3-1. assessment1_database.sql
Execute the following code, which includes the name of this file, on your local machine, and it will restore the whole database on your MySQL;
mysql -u username -p assessment1 < assessment1_database.sql
## 3-2. queries.sql
Execute the SQL queries in the file and it will retrieve the certain information specified in the task.
## 3-3. ERD.png
You can refer to the ERD in this file to understand the structure of the database and the relationships between each table.

# 4. AI usage declaration
## 4-1. Purpose
In this assessment, I used a generative AI, which is Chat GPT, to develop ideas, help me understand key concepts, theories, and error messages in coding.
## 4-2. Details
|     | Hyperlinks                                               | prompt                                                                                                                                                                                                                                                                                                                                                                                                                                      | reference                                                                                                                                                                                                                                                | 
| --- | -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | 
| 1   | https://chatgpt.com/s/t_6a2fe4072cc88191b4f8b94df16e36eb | What exactly is VARCHAR(150) an abbreviation of, in specifying data types in each column within CREATE TABLES command in MySQL? Also, tell me other possible data type                                                                                                                                                                                                                                                                      | To help further understand datatypes in columns                                                                                                                                                                                                          | 
| 2   | https://chatgpt.com/s/t_6a2fe41719b4819188ca7e44feb91416 | In MySQL, when creating an empty table to load data which may contain missing values into and specifying conditions for each column, unless I am certain that there is no missing value in a certain column, is it okay to let NULL in the column?                                                                                                                                                                                          | To assist with creating tables to load the provided csv files(, which I was not certain whether they have missing values in them) , particularly the part of defining each column's datatype (NULL or NOT NULL)&nbsp; in creating a newdatabase in MySQL | 
| 3   | https://chatgpt.com/s/t_6a2fe42eea5c81918726747535b3909e | Can a primary key and foreign key have different names(of columns) even though they indicate the practically same column?                                                                                                                                                                                                                                                                                                                   | To help understand a primary key and foreign key can have different names,&nbsp; when trying to integrate the two tables of doctors and patients                                                                                                         | 
| 4   | https://chatgpt.com/s/t_6a2fe43e5a84819183670ce0aebc62f4 | How can I distinguish between columns of the same name in different tables when creating tables in MySQL? For example, how can I distinguish between name in patients table meaning patient's name, and name in doctors table meaning doctor's name, in the output?                                                                                                                                                                         | To help make a SQL command which&nbsp;distinguishes several columns with the same names                                                                                                                                                                  | 
| 5   | https://chatgpt.com/s/t_6a2fe481f08081918de0191dbd78df1d | The following command only outputs an empty table. Why is it unable to output a file with loaded data? Note that (file location) represents the location of the directory of file I want to load, and (columns) represents the list of columns of data in the loaded file; mysql> LOAD DATA LOCAL INFILE '(file location)' INTO TABLE hospitals FIELDS TERMINATED BY '\t' IGNORE 1 LINES (columns); mysql› SELECT * FROM hospital LIMIT 5; | To help understand that specifying different delimiters (',' or 'tab') from the ones in the original csv files can lead to error message when loading data into tables                                                                                   | 
| 6   | https://chatgpt.com/s/t_6a2fe49e1bc881919105ec574fbc913b | In My SQL, does INT unsigned really represent integers equal to or greater than zero, or does it only represent integers equal to or greater than one, in the context where the values in id columns of loaded tables starts with 1, not zero.                                                                                                                                                                                              | To help understand INT unsigned always represents integers equal to or greater than zero.                                                                                                                                                                | 
| 7   | https://chatgpt.com/s/t_6a2fe4b36740819186a2c5dc26d54a0f | In MySQL, if the values of id columns in an original csv file were to start with 0, not 1, would INT unsigned AUTO_INCREMENT reflect it in the output?                                                                                                                                                                                                                                                                                      | To help understand AUTO_INCREMENT does not always regulate numbers, but it generates them only when they are not provided in the original data.                                                                                                          | 
| 8   | https://chatgpt.com/s/t_6a2fe4c89f3081919029f50cec92abe8 | In a command which includes the following part ; 'SELECT doctors.person_id ON doctors.hospital_id = hospitals.hospital_id WHERE hospital_id = 1; what does ' WHERE clause ambiguous' mean in the error message?                                                                                                                                                                                                                             | To understand the need to distinguish columns which are common among multiple tables and help recognize the rule of execution orders in SQL that WHERE is executed before ON.                                                                            | 
| 9   | https://chatgpt.com/s/t_6a2fe4e7ede88191a3e21bb3c3c7b582 | Why does the following command return an error message?; SELECT doctors.*, prescriptions.prescription_id, COUNT (*) FROM doctors INNER JOIN prescriptions ON doctors.person_id = prescriptions.doctor_id GROUP BY doctors.person_id ORDER BY COUNT (*) DESC LIMIT 3;                                                                                                                                                                        | To help understand columns specified in SELECT need to be those included in GROUP BY, or aggregate function such as COUNT                                                                                                                                | 

## 5. Hyperlink of this GitHub repository
https://github.com/sawachan38/assessment1_submission 


