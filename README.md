## DEVELOPED BY : SANTHANA LAKSHMI K
## REG NO. : 212222240091
## Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.


### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.

   
### PROGRAM:
```
DEVELOPED BY: SANTHANA LAKSHMI K
REG NO 212222240091
```
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
file_path = '/content/powerconsumption.csv'
data = pd.read_csv(file_path)

# Extract the 'PowerConsumption_Zone1' column
power_consumption = data['PowerConsumption_Zone1'].dropna()

# Mean
data_mean = np.mean(power_consumption)

# Variance
data_var = np.var(power_consumption)

# Normalized data
normalized_data = (power_consumption - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')

# Take only the positive lags
acf_result = acf_result[len(acf_result)//2:]

# Plot the ACF
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36], use_line_collection=True)
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) for Power Consumption (Zone 1)')
plt.show()
```


### OUTPUT:

![image](https://github.com/user-attachments/assets/ba660747-d2e1-4a0a-80c1-9e0596b92a26)



### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
