# Ex.No: 1B CONVERSION OF NON STATIONARY TO STATIONARY DATA
### Date: 19.08.2025
### Reg No:212223240182
### Name:VINOTH M P
### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data = pd.read_csv("/content/test.csv") 
data.set_index('id', inplace=True)
series = data['ram']
data['ram_diff'] = series - series.shift(1)
result = seasonal_decompose(series, model='additive', period=12)
data['ram_sea_diff'] = result.resid
data['ram_log'] = np.log(series)
data['ram_log_diff'] = data['ram_log'] - data['ram_log'].shift(1)
result = seasonal_decompose(data['ram_log_diff'].dropna(), model='additive', period=12)
data['ram_log_seasonal_diff'] = result.resid
plt.figure(figsize=(16, 16))
plt.subplot(6, 1, 1)
plt.plot(series, label='Original')
plt.legend(loc='best')
plt.title('Original Data')
plt.xlabel('ID')
plt.ylabel('RAM')
plt.subplot(6, 1, 2)
plt.plot(data['ram_diff'], label='Regular Difference')
plt.legend(loc='best')
plt.title('Regular Differencing')
plt.subplot(6, 1, 3)
plt.plot(data['ram_sea_diff'], label='Seasonal Adjustment')
plt.legend(loc='best')
plt.title('Seasonal Adjustment')
plt.subplot(6, 1, 4)
plt.plot(data['ram_log'], label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')
plt.subplot(6, 1, 5)
plt.plot(data['ram_log_diff'], label='Log Transformation + Differencing')
plt.legend(loc='best')
plt.title('Log Transformation + Regular Differencing')
plt.subplot(6, 1, 6)
plt.plot(data['ram_log_seasonal_diff'], label='Log Transformation + Seasonal Differencing')
plt.legend(loc='best')
plt.title('Log Transformation + Regular + Seasonal Differencing')
plt.tight_layout()
plt.show()
data['ram'].plot(kind='line', figsize=(10,5), title="RAM Time Series")
plt.show()
```


### OUTPUT:

ORIGINAL DATA:

<img width="1608" height="258" alt="image" src="https://github.com/user-attachments/assets/705ce139-ee27-4fcb-97af-16f871f10f71" />

REGULAR DIFFERENCING:

<img width="1566" height="250" alt="image" src="https://github.com/user-attachments/assets/6ab157a3-03f2-4fc8-9d68-c793c3cd5beb" />

SEASONAL ADJUSTMENT:

<img width="1612" height="258" alt="image" src="https://github.com/user-attachments/assets/f4b5bfe2-9902-4ce6-b770-90c37b5e49c6" />

LOG TRANSFORMATION:

<img width="1589" height="247" alt="image" src="https://github.com/user-attachments/assets/5111c1fe-f9a1-4e50-ba09-e63fa8def16a" />

LOG TRANSFORMATION + REGULAR DIFFERENCING:

<img width="1620" height="267" alt="image" src="https://github.com/user-attachments/assets/9fa29650-38a4-4f77-8d41-6e3df1c309a9" />

LOG TRANSFORMATION + REGULAR + Seasonal DIFFERENCING:

<img width="1575" height="272" alt="image" src="https://github.com/user-attachments/assets/e1bc4e50-f3ad-453c-be12-bddae23c4635" />

### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
