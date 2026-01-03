# Ex.05 Design a Website for Server Side Processing
## Date:

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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
```
math.html
<!DOCTYPE>
<html>
<head>
    <title>Power Calculation</title>
<style>
body {
    background-color: #00ff11;
}
.edge {
    width: 100%;
    padding-top: 250px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick dashed #ffffff;
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: rgb(23, 53, 222);
}
.formelt {
    color: rgb(9, 10, 11);
    text-align: center;
    margin-top: 7px;
    margin-bottom: 6px;
}
h1 {
    color: rgb(227, 176, 11);
    padding-top: 20px;
}

</style>
</head>
<body>

    <h2>Calculate Power (P = I² × R)</h2>

    <form method="POST">
        {% csrf_token %}
        
        <label for="current">Current (I in Amps):</label><br>
        <input type="text" id="current" name="current" placeholder="Enter current"><br>

        <label for="resistance">Resistance (R in Ohms):</label><br>
        <input type="text" id="resistance" name="resistance" placeholder="Enter resistance"><br>

        <input type="submit" value="Calculate Power">
    </form>

    {% if power %}
        <div class="result">
            Power = {{ power }} Watts
        </div>
    {% endif %}

    {% if error %}
        <div class="error">
            Error: {{ error }}
        </div>
    {% endif %}

</body>
</html>

views.py
from django.shortcuts import render

def calculate_power(request):
    power = None
    error = None

    if request.method == 'POST':
        print("Request method is used")

        try:
            current = float(request.POST.get('current'))
            resistance = float(request.POST.get('resistance'))

            power = (current ** 2) * resistance

            print("Current:", current)
            print("Resistance:", resistance)
            print("Power:", power)

        except (TypeError, ValueError):
            error = "Please enter valid numeric values."
            print("Invalid input received.")

    return render(request, 'mathapp/math.html', {
        'power': power,
        'error': error
    })

urls.py
from django.contrib import admin
from django.urls import path
from mathapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.calculate_power, name='calculate_power') # root URL
]
```

## SERVER SIDE PROCESSING:

<img width="617" height="320" alt="ex_5" src="https://github.com/user-attachments/assets/262cc38d-276d-48d2-9aa3-c6a432677efa" />


## HOMEPAGE:
<img width="1860" height="923" alt="Screenshot 2025-12-19 090031" src="https://github.com/user-attachments/assets/5e3b0fcf-2900-4b1a-821f-0e069e1d43a8" />


## RESULT:
The program for performing server side processing is completed successfully.
