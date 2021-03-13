# Anomaly Detection in Time Series Data with Keras

We design and train an LSTM autoencoder using the Keras API with Tensorflow 2 as the backend to detect anomalies (sudden price changes) in the S&amp;P 500 index and create interactive charts and plots with Plotly and Seaborn.

## What is anomaly detection?
Anomaly detection is any process that finds the outliers of a dataset; those items that don’t belong. These anomalies might point to unusual network traffic, uncover a sensor on the fritz, or simply identify data for cleaning, before analysis.

### In enterprise IT, anomaly detection is commonly used for:
Data cleaning
Intrusion detection
Fraud detection
Systems health monitoring
Event detection in sensor networks
Ecosystem disturbances

# In this project:

## Objectives:
1.	Build an LSTM Autoencoder in Keras
2.	Detect anomalies with Autoencoders in time series data
3.	Create interactive charts and plots with Plotly and Seaborn

## Steps:
•	1: Import Libraries
•	2: Load and Inspect the S&P 500 Index Data
•	3: Data Preprocessing
•	4: Temporalize Data and Create Training and Test Splits
•	5: Build an LSTM Autoencoder
•	6: Train the Autoencoder
•	7: Plot Metrics and Evaluate the Model
•	8: Detect Anomalies in the S&P 500 Index Data

### 1. Part
Import the libraries

### 2. Part
Inspect the S&P 500 data from 190 to 2010
2 columns of data : date(x axis) and closing price(y axis)
Parse the date into Pandas date times format.
Use plotly to see interactive line chart to zoom and see the spesific time via plotly_graph.
Note that scatter plot also provides an argument to shose time mode type and we will choose 'lines' (markers)
update_layout creates interactive plot and 'showlegend' lets us to see label for the spesific time.

### 3. Part
For preprocessing divide the data as train/test as 8/2
Divide dataframe into 2 by the lenght of the train size will be the first part
Scale the data with sklearn via standartscaler
Fit the scaler helper fuction to train to make it learn the statistics use scaler.fit and transform it

### 4. Part
Create sequennces because it is times series and we have to resahepe our data because we will use LSTM
number of features is 1
instead of multiply same operation many times, just create a fuction to eliminate the repetition
loop in the time steps
return it in array format

### 5. Part
set the parameters first
arrange the time steps as 30
num_features: is 1
sequential means is list of layer.
Repeat vector dublicate the encoder and built a bridge between endocer and decoder
Time distributer dublicate the output from the decoder and created 128 + 1 layer
compile with loss fuction = mae and optimized it via adam

### 6. Part
Allow the early stopping by monitoring the improvement via 'val_loss'

### 7. Part
Visialisation to see the train loss and validation loss plot
to test the model we will calculate the mean absolute error(mae)
and evaluate the error and plot it

### 8. Part
Set the anomaly category where loss is higher than our threshold as 0.65.
Finally create 2 graph:
an interactive plot including loss score with our threshold
and
inversed closing prices line plot with detected anomalies in scatter form(mode=markers)
