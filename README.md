# Ex.05 Design a Website for Server Side Processing
# Date:27.11.2025
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
```
<html>
<head>
    <title>Power Calculation</title>

    <style>

        body{
            text-align: center;
            height:100vh;
            display:flex;
            justify-content:center;
            align-items:center;
            background: linear-gradient(135deg, #e49de3 0%, #efef6e 100%);
            font-family: "Poppins", sans-serif;
        }

        .one{
            width: 400px;
            padding: 40px;
            backdrop-filter: blur(12px);
            background: rgba(42, 228, 22, 0.1);
            border-radius: 18px;
            border:1px solid rgba(46, 228, 49, 0.35);
            box-shadow: 0 8px 25px rgba(35, 220, 18, 0.4);
            
        }

        h1{
            font-size: 38px;
            color: #a02727;
            margin-bottom: 20px;
        }

        label{
            font-size: 20px;
            color:#160202;
            text-align:left;
        }

        input{
            padding:10px;
            width:90%;
            border:none;
            margin-top:10px;
            background:rgba(5, 5, 5, 0.18);
            border-radius:8px;
            color:rgb(19, 14, 10);
            outline:none;
        }

        button{
            width:100%;
            margin-top:15px;
            padding:10px;
            border:none;
            border-radius:10px;
            cursor:pointer;
            background:#d52825;
            color:rgb(190, 86, 86);
            font-size:17px;
            
        }

        button:hover{
            background:#ff8767;
        }
    </style>
</head>

<body>

<div class="one">
<h1>Power Calculator</h1><br>

<form method="POST">
    {% csrf_token %}

    <label>Intensity:
        <input type="number" name="intensity" required placeholder="Enter in cd"><br><br>
    </label>

    <label>Resistance:
        <input type="number" name="resistance" required placeholder="Enter in Ohms"><br><br>
    </label>

    <button type="submit">Calculate</button><br><br>

    <label>Power:</label>
    <input type="text" value="{{ power }}" readonly> <pre> Watts </pre>

</form>
</div>
</body>
</html>
```
```
urls.py

from django.contrib import admin
from django.urls import path
from powerapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.power,name='power'),
    
]
```
```
views.py

from django.shortcuts import render
def power(request):
    power=''
    if request.method == "POST":
        intensity = float(request.POST.get("intensity"))
        resistance = float(request.POST.get("resistance"))
        power=intensity**2*resistance
        print(f"Intensity: {intensity}, Resistance: {resistance},Power:{power:.2f}")
    return render(request, 'math.html', {'power': power})

```
# SERVER SIDE PROCESSING:
<img width="961" height="486" alt="image" src="https://github.com/user-attachments/assets/e6d6d9da-8f1e-4d6c-a7b4-660184322535" />

# HOMEPAGE:
# RESULT:
The program for performing server side processing is completed successfully.
