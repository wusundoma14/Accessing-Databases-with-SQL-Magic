# Accessing Databases with SQL Magic/IBM Course
## Objectives
After completing this lab you will be able to:

1. Perform simplified database access using SQL "magic"
2. Query database using SQL "magic"
3. Assign query result to Python Variable
4. Convert query result to DataFrame


To communicate with SQL Databases from within a JupyterLab notebook, we can use the SQL "magic" provided by the ipython-sql extension. "Magic" is JupyterLab's term for special commands that start with "%". Below, we'll use the load__ext_ magic to load the ipython-sql extension. In the lab environemnt provided in the course, the ipython-sql extension is already installed.


To install ipython-sql extension, run the script below in a code cell:

!pip install ipython-sql


The above magic command loads the ipython-sql extension. We can connect to any database which is supported by SQLAlchemy. Here we will connect to an existing MySQL database. However, in order to do that, you'll first need to retrieve your credentials and connect to your MySQL database.



import os 

from dotenv import load_dotenv
load_dotenv() 

myuser = os.environ.get('mysql_username')      # e.g. 'root'
mypassword= os.environ.get('mysql_password')   # e.g. 'sample-password' 

connection_url = 'mysql://{user}:{password}@localhost/ibm_sql_lab'.format(user=myuser,password=mypassword)

%sql {connection_url}


*If it gives an empty output or non error output, then you are connected to your MySQL Database* 
For convenience, we can use %%sql (two %'s instead of one) at the top of a cell to indicate we want the entire cell to be treated as SQL. Let's use this to create a table and fill it with some test data for experimenting.
