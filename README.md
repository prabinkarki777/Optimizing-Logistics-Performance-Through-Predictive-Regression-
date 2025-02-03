# Logistics Performance Prediction Analysis

## Logistics Performance Prediction Analysis

This repository contains code and analysis for predicting logistics performance using machine learning techniques.

## Project Overview
This project aims to analyze and predict logistics performance using different machine learning models. The key steps involved include:
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Model Training & Evaluation

## Installation
To run this project, install the required dependencies:

```bash
pip install -r requirements.txt
```

## Usage
Run the Jupyter Notebook to execute the analysis step by step.

```bash
jupyter notebook Logistics_Performance_Prediction_Analysis.ipynb
```

## Code Example
Here is a brief example of the code used in this project:

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, isnan, when, count, lit, radians, sin, cos, atan2, sqrt, dayofweek, hour, minute
from pyspark.sql import functions as F

# Configure Spark session
spark = SparkSession.builder \
    .master("local[10]") \
    .appName("NoBroadcastApp") \
    .config("spark.driver.memory", "30g") \
    .config("spark.executor.memory", "30g") \
    .config("spark.executor.cores", "10") \
    .config("spark.sql.shuffle.partitions", "500") \
    .config("spark.sql.autoBroadcastJoinThreshold", -1) \
    .config("spark.broadcast.compress", "false")  \
    .config("spark.broadcast.blockSize", "4m")  \
    .getOrCreate()
```

```python
# Load Dataset
file_path = "data/amazon_delivery.csv"
data = spark.read.csv(file_path, header=True, inferSchema=True).coalesce(1)
data.createOrReplaceTempView("amazon_delivery")

```

## Results
The project includes comparative analysis of multiple regression models to assess logistics performance.

## Author
Your Name

## License
This project is licensed under the MIT License.
