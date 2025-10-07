# Ex.05 Design a Website for Server Side Processing
## Date:07/10/2025

## AIM:


 To design a website to calculate the BMI.



## FORMULA:

BMI =W/H<sup>2 
<br> W-->Weight
<br> H-->Height
<br> 



## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :

math.html

<html>
<head>
    <title>BMI Calculator</title>
    <style>
        body {
            font-family: "Segoe UI", sans-serif;
            margin: 0;
            padding: 0;
            color: black;
        }

        .container {
            width: 400px;
            margin: 70px;
            background: white;
            border-radius: 15px;
            padding: 30px;
            text-align: center;
        }
        h1 {
            color: blue;
            margin-bottom: 10px;
        }

        h3 {
            color: brown;
            margin-bottom: 25px;
        }

        label{
            text-align: left;
            margin-top: 15px;
            font-weight: bold;
        }

        input[type="text"] {
            width: 100%;
            padding: 10px;
            margin-top: 8px;
            border: 2px solid red;
            border-radius: 8px;
            font-size: 16px;
        }

        input[type="submit"] {
            background: yellow;
            color: greenyellow;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            font-size: 16px;
            margin-top: 20px;
        }

        input[type="submit"]:hover {
            background: green;
            transform: scale(1.05);
        }

        .result {
            margin-top: 25px;
            padding: 15px;
            background: red;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>BMI CALCULATOR</h1>
        <h2>Sachin J M(25007184)</h2>

        <form method="post">
            {% csrf_token %}
            <label for="height">Height (cm):</label>
            <input type="text" id="height" name="height" value="" required>

            <label for="weight">Weight (kg):</label>
            <input type="text" id="weight" name="weight" value="" required>

            <input type="submit" value="Calculate BMI">
        </form>
        <div class="result">
            <h2>Your BMI: {{ bmi }}</h2>
        </div>
</body>
</html>

urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('bmi/',views.calculate_bmi,name="bmi"),
    path('',views.calculate_bmi,name="bmicalculator")
]

views.py


from django.shortcuts import render
def calculate_bmi(request):
    context={}
    context['bmi']="0"
    context['w']="0"
    context['h']="0"
    if(request.method=='POST'):
       w= float(request.POST.get('weight','0'))
       h=float(request.POST.get('height','0'))
       print('request=',request)
       
       print('Weight=',w)
       print('Height=',h)
       bmi=w/((h/100)**2)
       context['bmi']=bmi
       context['w']=w
       context['h']=h
       print('BMI=',bmi)
    return render(request,'mathapp/math.html',context)







## SERVER SIDE PROCESSING:


## HOMEPAGE:


## RESULT:
The program for performing server side processing is completed successfully.
