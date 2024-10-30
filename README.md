# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Data Preparation: Load data, handle missing values, and extract relevant features for clustering.

2.Determine Clusters: Use the Elbow Method to find optimal number of clusters based on WCSS.

3.K-Means Clustering: Fit the K-Means model with optimal clusters, predict cluster labels for data.

4.Visualization: Plot data points with distinct colors for each cluster to visualize clustering resulta

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Suryamalarv
RegisterNumber:  212223230224
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("/content/Mall_Customers.csv")
```
```
data.head()
```
![image](https://github.com/user-attachments/assets/0d6b2169-b009-4ed0-81c3-cf7d245c9fdc)
```
data.info()
```
![image](https://github.com/user-attachments/assets/1b5577fa-ec27-4671-995c-e9ba3d7b8223)
```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/0c15135f-4ef2-41a0-be88-a682cf5fe418)
```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
  kmeans = KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("no of cluster")
plt.ylabel("wcss")
plt.title("Elbow Metthod")
```
![image](https://github.com/user-attachments/assets/b69d7332-b36a-48ee-bdca-37a7197ced32)
```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
```
![image](https://github.com/user-attachments/assets/da1a26fe-224e-4c56-8208-cd830c10cc08)
```
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
```
```
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segmets")
```
# OUTPUT
![image](https://github.com/user-attachments/assets/968ddd2d-bb44-48c9-9ab3-0e401158d92b)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
