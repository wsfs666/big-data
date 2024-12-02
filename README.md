# big-data
STEPS TO FORM A CLUSTER

To register master: 
1. Open spark-env.sh file

>>> code $SPARK_HOME/conf/spark-env.sh
2. Add the exports in the file

export SPARK_MASTER_HOST= 10.100.153.25
export SPARK_LOCAL_IP= 10.100.153.25

3. Start master
$SPARK_HOME/sbin/start-master.sh
To stop the master

$SPARK_HOME/sbin/stop-master.sh
Edit workers:

sudo code $HADOOP_HOME/etc/hadoop/workers
4. Register worker nodes
For mac:
$SPARK_HOME/sbin/start-worker.sh spark://10.100.153.25:7077

For windows:
cd C:/spark/spark/sbin> start-worker.sh spark://10.100.153.25:7077

5. open the url:
for master node
http://fuxiaosidembp-2.lakeheadu.ca:8080

 worker node:1
http://asmas-air.lakeheadu.ca:8081
 
worker node:2
http://desktop-eq55q8h.lakeheadu.ca:8082

 
6. open jupyter notebook
Create a spark session:
Line1: from pyspark.sql import SparkSession
Line2: spark = SparkSession.builder \
      .master("spark://10.100.72.153:7077") \
      .appName("lakehead_University_Enrollement_Trends") \
      .getOrCreate()

7. To connect to mongodb:
(base) asmaulhusna@asmas-air bin % mongoshtest> use big_data
switched to db big_data
big_data> db.createCollection("big_data_project")
{ ok: 1 }

big_data> exit
(base) asmaulhusna@asmas-air bin % mongoimport --db big_data --collection lakehead_enrollment --type csv –file /Users/asmaulhusna/big_data/lakehead_University_Student_Enrollment_trends/lakehead_dataset.csv  --headerline

test> use big_data
switched to db big_data
big_data> db.lakehead_enrollment.find().limit(5)
 

In jupyter notebook:

Line3: 
from pymongo import MongoClient
# Connect to MongoDB running on localhost
client = MongoClient('mongodb://localhost:27017/')
# Connect to the 'big_data' database
db = client['big_data']
# Access the 'lakehead_enrollment' collection
collection = db['lakehead_enrollment']
 
Line4:
import pandas as pd
# Retrieve all documents from the collection
data = collection.find()
# Convert the data to a Pandas DataFrame
df = pd.DataFrame(list(data))
# Display the first few rows
df.head()




SUCCESSFULLY RUNNING JOBS
 
    
        


        


![image](https://github.com/user-attachments/assets/fe25b449-8b0f-416e-83da-d31b0a7cb840)
