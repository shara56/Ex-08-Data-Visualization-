# Ex-08-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```
#Import required libraries

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

#Load the dataset

df = pd.read_csv('Superstore2.csv', encoding='unicode_escape')

#Data Cleaning: Drop unnecessary columns

df.drop(['Row ID', 'Order ID', 'Ship Date', 'Customer ID', 'Postal Code', 'Product ID'], axis=1, inplace=True)

#Feature Generation: Extract Year and Month from Order Date

df['Year'] = pd.DatetimeIndex(df['Order Date']).year

df['Month'] = pd.DatetimeIndex(df['Order Date']).month_name()

#1. Which Segment has Highest sales?

segment_sales = df.groupby('Segment')['Sales'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Segment', y='Sales', data=segment_sales)

plt.title('Segment-wise Sales')

plt.show()

#2. Which City has Highest profit?

city_profit = df.groupby('City')['Profit'].sum().reset_index().sort_values(by='Profit', ascending=False)

plt.figure(figsize=(12,8))

sns.barplot(x='City', y='Profit', data=city_profit.head(10))

plt.title('Top 10 Cities by Profit')

plt.show()

#3. Which ship mode is profitable?

shipmode_profit = df.groupby('Ship Mode')['Profit'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Ship Mode', y='Profit', data=shipmode_profit)

plt.title('Ship Mode-wise Profit')

plt.show()

#4. Sales of the product based on region

region_sales = df.groupby('Region')['Sales'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Region', y='Sales', data=region_sales)

plt.title('Region-wise Sales')

plt.show()

#5. Find the relation between sales and profit

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', data=df)

plt.title('Sales vs. Profit')

plt.show()

#6. Find the relation between sales and profit based on the following category.

#i) Segment

segment_sales_profit = df.groupby('Segment')['Sales', 'Profit'].mean().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Segment', y='Sales', data=segment_sales_profit, color='blue', alpha=0.5, label='Sales')

sns.barplot(x='Segment', y='Profit', data=segment_sales_profit, color='green', alpha=0.5, label='Profit')

plt.title('Segment-wise Sales and Profit')

plt.legend()

plt.show()

#ii) City

city_sales_profit = df.groupby('City')['Sales', 'Profit'].mean().reset_index().sort_values(by='Profit', ascending=False).head(10)

plt.figure(figsize=(12,8))

sns.barplot(x='City', y='Sales', data=city_sales_profit, color='blue', alpha=0.5, label='Sales')

sns.barplot(x='City', y='Profit', data=city_sales_profit, color='green', alpha=0.5, label='Profit')

plt.title('Top 10 Cities by Sales and Profit')

plt.legend()

plt.show()

#iii) States

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='State', data=df)

plt.title('Sales vs. Profit based on State')

plt.show()

#iv) Segment and Ship Mode

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='Segment', style='Ship Mode', data=df)

plt.title('Sales vs. Profit based on Segment and Ship Mode')

plt.show()

#v) Segment, Ship mode and Region

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='Segment', style='Ship Mode', size='Region', data=df)

plt.title('Sales vs. Profit based on Segment, Ship Mode and Region')

plt.show()
```
# OUPUT

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/5d00d634-8715-4132-a1b3-beaf01d3704f)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/6a75d69f-7f43-4487-8143-d0997fc1570d)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/4b8238ef-09b1-4224-b680-c4f2140d17fd)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/c4b3b709-09be-4d4b-b4c1-491662365762)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/896ff3d6-1948-4cb7-a3e1-f2a629ec1802)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/ea086cc0-fa08-4b05-a3b6-931a97eee232)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/3080b6b8-7b4d-491b-82b4-ba2359d6d763)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/bdafc0a3-d0b2-43ef-8d8d-86979fb06ffd)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/8e6bc8e1-45e5-4e4c-be9d-71c5d72cfc1e)

![image](https://github.com/shara56/Ex-08-Data-Visualization-/assets/113497104/cf6096bc-cde4-4809-ab18-8b94a6917556)

# RESULT:

Thus, to Perform Data Visualization on the given dataset and save the data to a file has been successfully performed.
