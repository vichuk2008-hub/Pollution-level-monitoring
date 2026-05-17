# Import Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Create Sample Pollution Dataset
pollution_data = {
    'Record_ID': [1,2,3,4,5,6,7,8,9,10,11,12],

    'Station_Name': ['Chennai','Chennai','Chennai','Chennai',
                     'Delhi','Delhi','Delhi','Delhi',
                     'Mumbai','Mumbai','Mumbai','Mumbai'],

    'Location': ['South','South','South','South',
                 'North','North','North','North',
                 'West','West','West','West'],

    'Month': ['Jan','Apr','Jul','Oct',
              'Jan','Apr','Jul','Oct',
              'Jan','Apr','Jul','Oct'],

    'AQI': [120,150,180,160,
            200,250,320,280,
            140,170,210,190],

    'PM2_5': [45,55,70,60,
              80,95,120,100,
              50,65,85,75],

    'PM10': [90,110,130,120,
             150,180,220,200,
             100,125,160,145],

    'CO_Level': [0.8,1.0,1.2,1.1,
                 1.5,1.8,2.2,2.0,
                 1.0,1.2,1.5,1.3],

    'NO2_Level': [25,30,40,35,
                  50,60,75,65,
                  35,40,50,45]
}

# Create DataFrame
df = pd.DataFrame(pollution_data)

# Display Dataset
print("\nPollution Dataset\n")
print(df)

# Check Missing Values
print("\nMissing Values\n")
print(df.isnull().sum())

# Basic Statistics
print("\nBasic Pollution Statistics\n")
print(df[['AQI', 'PM2_5', 'PM10']].describe())

# NumPy Statistics
aqi_array = np.array(df['AQI'])

print("\nNumPy AQI Statistics:\n")
print(f"Mean AQI : {np.mean(aqi_array):.2f}")
print(f"Maximum AQI : {np.max(aqi_array)}")
print(f"Minimum AQI : {np.min(aqi_array)}")

# Monthly Average AQI
monthly_aqi = df.groupby('Month')['AQI'].mean()

print("\nMonthly Average AQI\n")
print(monthly_aqi)

# Maximum AQI by Station
max_aqi = df.groupby('Station_Name')['AQI'].max()

print("\nMaximum AQI by Station\n")
print(max_aqi)

# Pivot Table
pivot = pd.pivot_table(
    df,
    values='AQI',
    index='Station_Name',
    columns='Month',
    aggfunc=np.mean
)

print("\nPivot Table - AQI Analysis\n")
print(pivot)

# Visualization 1 – Average AQI by Month
plt.figure(figsize=(7,4))
monthly_aqi.plot(kind='bar', color='orange')

plt.title('Average AQI by Month')
plt.xlabel('Month')
plt.ylabel('AQI')
plt.grid(axis='y')
plt.tight_layout()
plt.show()

# Visualization 2 – AQI Trend by Station
plt.figure(figsize=(8,4))

for station in df['Station_Name'].unique():
    subset = df[df['Station_Name'] == station]

    plt.plot(
        subset['Month'],
        subset['AQI'],
        marker='o',
        label=station
    )

plt.title('AQI Trend by Station')
plt.xlabel('Month')
plt.ylabel('AQI')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()

print("\nPollution Level Monitoring Completed Successfully")
