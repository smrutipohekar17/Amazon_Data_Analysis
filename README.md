# Amazon Product Reviews Analysis

This repository contains a comprehensive analysis of Amazon product review data. The analysis involves data preparation, user recommendation analysis, product popularity analysis, viewer behavior analysis, verbosity analysis, and sentiment analysis.

## Table of Contents

1. [Introduction](#introduction)
2. [Objective](#objective)
3. [Dataset](#dataset)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Analysis Steps](#analysis-steps)
   - [1. Reading Data from SQLite Database](#1-reading-data-from-sqlite-database)
   - [2. Data Preparation](#2-data-preparation)
   - [3. User Recommendation Analysis](#3-user-recommendation-analysis)
   - [4. Popular Products Analysis](#4-popular-products-analysis)
   - [5. Viewer Behavior Analysis](#5-viewer-behavior-analysis)
   - [6. Verbosity Analysis](#6-verbosity-analysis)
   - [7. Sentiment Analysis](#7-sentiment-analysis)
7. [Visualizations](#visualizations)
8. [Conclusion](#conclusion)

## Introduction

This project aims to analyze Amazon product reviews to gain insights into user behavior, product popularity, and review sentiments. The dataset includes features such as user and product IDs, review texts, helpfulness metrics, and ratings.

## Objective
The primary objectives of this analysis are:

- Data Preparation: Clean and prepare the data for analysis.
- User Recommendation Analysis: Identify users who are likely to purchase more products based on their review activity.
- Popular Products Analysis: Determine which products are most frequently reviewed and identify the products with the highest number of reviews.
- Viewer Behavior Analysis: Compare the behaviors of frequent and non-frequent reviewers to understand differences in review patterns and ratings.
- Verbosity Analysis: Analyze the verbosity of reviews to see if frequent reviewers tend to write longer reviews.
- Sentiment Analysis: Perform sentiment analysis on review summaries to determine the overall sentiment expressed in the reviews.

## Dataset

The dataset used in this analysis is stored in a SQLite database named `database.sqlite`. It contains the following features:

- `Id`: Unique identifier for the review
- `ProductId`: Unique identifier for the product
- `UserId`: Unique identifier for the user
- `ProfileName`: Profile name of the user
- `HelpfulnessNumerator`: Number of users who found the review helpful
- `HelpfulnessDenominator`: Number of users who indicated whether they found the review helpful or not
- `Score`: Rating between 1 and 5
- `Time`: Timestamp for the review
- `Summary`: Brief summary of the review
- `Text`: Text of the review

The dataset is available [here](https://drive.google.com/drive/folders/1mQzRTzBkXK21XkXsqShm8-KATZ9ojb5k?usp=sharing).

## Usage

To run the analysis, execute the provided Jupyter Notebook or Python script. Make sure the `database.sqlite` file is in the project directory.

## Analysis Steps

### 1. Reading Data from SQLite Database

Connect to the SQLite database and read the data into a pandas DataFrame.

```python
import sqlite3
import pandas as pd

# Create a SQL connection to the SQLite database
con = sqlite3.connect('database.sqlite')

# Reading data from the SQLite database
df = pd.read_sql_query("SELECT * FROM REVIEWS", con)

# Checking the dimensions of the dataframe
df.shape
```

### 2. Data Preparation

Clean and prepare the data for analysis:
- Remove invalid rows where `HelpfulnessNumerator` is greater than `HelpfulnessDenominator`.
- Remove duplicate rows based on `UserId`, `ProfileName`, `Time`, and `Text`.
- Convert the `Time` feature from an integer to a datetime format.

### 3. User Recommendation Analysis

Identify users to whom Amazon can recommend more products by aggregating data to get the number of summaries, texts, average score, and products purchased by each user.

### 4. Popular Products Analysis

Identify the most reviewed products by counting the number of reviews for each product and filtering those with more than 500 reviews.

### 5. Viewer Behavior Analysis

Compare the behavior of frequent viewers (those who bought products 50 times or more) versus non-frequent viewers (those who bought less than 50 times).

### 6. Verbosity Analysis

Analyze if frequent users are more verbose by comparing the length of their reviews.

### 7. Sentiment Analysis

Perform sentiment analysis on review summaries to determine if the sentiment expressed is positive or negative.

## Visualizations

Several visualizations are created to support the analysis, including:
- Bar plots for top users.
- Count plots for most sold products.
- Box plots for text length comparison.

## Conclusion

The analysis provides insights into various aspects of the dataset, including:
- Identifying top users for product recommendations.
- Determining the most reviewed products.
- Understanding the behavior differences between frequent and non-frequent reviewers.
- Analyzing verbosity among reviewers.
- Performing sentiment analysis to understand the general sentiment expressed in reviews.

The analysis of Amazon product reviews has yielded several valuable insights. By identifying the top users who are most likely to purchase more products, we can enhance personalized marketing strategies and improve product recommendations. The analysis of popular products has provided an understanding of market trends and consumer preferences, which can guide inventory and sales strategies. The comparison between frequent and non-frequent reviewers revealed that frequent reviewers tend to give more moderate and detailed reviews, suggesting they are more discerning and possibly more reliable. Additionally, the sentiment analysis of review summaries has highlighted overall customer satisfaction and pinpointed areas for improvement. These insights collectively can help Amazon optimize their recommendation systems, better understand customer behavior, and ultimately enhance customer satisfaction and loyalty.

