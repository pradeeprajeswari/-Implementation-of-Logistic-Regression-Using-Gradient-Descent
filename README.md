# Implementation-of-Logistic-Regression-Using-Gradient-Descent

## AIM:
To write a program to implement the the Logistic Regression Using Gradient Descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load the dataset and remove unnecessary columns (sl_no and salary).
2. Convert relevant columns to categorical data types, then encode them as numerical codes.
3. Separate the dataset into features (X) and target (Y).
4. Initialize random weights (theta) for the model.
5. Define a sigmoid function for logistic regression and a loss function to calculate the model error.
6. Implement gradient descent to iteratively update theta based on the learning rate and the gradient.
7. Train the model by running gradient descent for a set number of iterations.
8. Define a prediction function that uses theta to classify new data.
9. Calculate and print the model's accuracy by comparing predictions to actual values in Y.
10. Predict and print the model's output for two new data samples (xnew).

## Program:
```
/*
Program to implement the the Logistic Regression Using Gradient Descent.
Developed by: PRADEEP. E
RegisterNumber:  212223230149
*/
```
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

dataset=pd.read_csv("C:/Users/admin/Downloads/Placement_Data.csv")
dataset

dataset=dataset.drop('sl_no',axis=1)
dataset=dataset.drop('salary',axis=1)

dataset["gender"]=dataset["gender"].astype('category')
dataset["ssc_b"]=dataset["ssc_b"].astype('category')
dataset["hsc_b"]=dataset["hsc_b"].astype('category')
dataset["degree_t"]=dataset["degree_t"].astype('category')
dataset["workex"]=dataset["workex"].astype('category')
dataset["specialisation"]=dataset["specialisation"].astype('category')
dataset["status"]=dataset["status"].astype('category')
dataset["hsc_s"]=dataset["hsc_s"].astype('category')
dataset.dtypes

dataset["gender"]=dataset["gender"].cat.codes
dataset["ssc_b"]=dataset["ssc_b"].cat.codes
dataset["hsc_b"]=dataset["hsc_b"].cat.codes
dataset["degree_t"]=dataset["degree_t"].cat.codes
dataset["workex"]=dataset["workex"].cat.codes
dataset["specialisation"]=dataset["specialisation"].cat.codes
dataset["status"]=dataset["status"].cat.codes
dataset["hsc_s"]=dataset["hsc_s"].cat.codes

dataset

X=dataset.iloc[:,:-1].values
Y=dataset.iloc[:,-1].values

Y

theta=np.random.randn(X.shape[1])
y=Y
def sigmoid(z):
    return 1 /(1+np.exp(-z))

def loss(theta,X,y):
    h=sigmoid(x.dot(theta))
    return -np.sum(y*np.log(h)+(1-y)*np.log(1-h))

def gradient_descent(theta,X,y,alpha,num_iterations):
    m=len(y)
    for i in range(num_iterations):
        h=sigmoid(X.dot(theta))
        gradient=X.T.dot(h-y)/m
        theta-=alpha*gradient
    return theta

theta=gradient_descent(theta,X,y,alpha=0.01,num_iterations=1000)

def predict(theta,X):
    h=sigmoid(X.dot(theta))
    y_pred=np.where(h>=0.5,1,0)
    return y_pred 

y_pred=predict(theta,X)

accuracy=np.mean(y_pred.flatten()==y)
print("Accuracy:",accuracy)

print(y_pred)

print(Y)

xnew=np.array([[0,87,0,95,0,2,78,2,0,0,1,0]])
y_prednew=predict(theta,xnew)
print(y_prednew)

xnew=np.array([[0,0,0,0,0,2,8,2,0,0,1,0]])
y_prednew=predict(theta,xnew)
print(y_prednew)
```
## Output:

![Screenshot 2024-10-18 105935](https://github.com/user-attachments/assets/cd299afb-4b0f-412b-affb-6e8c542b39f6)

![Screenshot 2024-10-18 105955](https://github.com/user-attachments/assets/67f22118-267c-41e8-94e6-5181ff20bf86)

![Screenshot 2024-10-18 105942](https://github.com/user-attachments/assets/de084307-1f44-4cf3-90c0-5050eed27561)


## Result:
Thus the program to implement the the Logistic Regression Using Gradient Descent is written and verified using python programming.

