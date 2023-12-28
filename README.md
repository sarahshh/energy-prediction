# Energy Consumption Classification and Prediction

## Project Objective

A new energy commercializing company in Colombia would like to define more dynamics pricing strategies. They want to be able to classify their customers according to their consumption level and offer price incentives to customers who are able to reduce their consumption during specific periods when demand is high.

## Methodology

The dataset provides hourly energy consumption for 233 meters in Colombia during 6 months. 
These meters are installed in flats that can be primary or secondary residence.
In order to classify consumers, we calculate mean daily consumption excluding days where consumption is below 4kWh (assumed to be days when property is vacant). K means algorithm was used to classify consumers in 3 clusters: low, medium, high.
For the prediction part, we used the prophet library which is well suited to times series data.

## Installation Instructions

The project is executed using Python and requires the installation of the following packages:
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- pytz
- prophet

These packages can be installed using pip :
```
pip install pandas numpy matplotlib seaborn scikit-learn pytz prophet
```

## How to use the dataset

The dataset is a csv file named "out.csv" that can be loaded using pandas library:
```
import pandas as pd

hourly_conso = pd.read_csv(path_to_file + '/out.csv')
```

## Results & Conclusions 

- Clients Classification: The classification algorithm provided 3 intervals of mean daily energy consumption (low, medium, high). A minority of households are in the high consumption Tier (13%). 
- Energy Prediction: We performed predictions for households belonging to the high Tier as they have a bigger influence on the total load and we looked at properties that were not vacant during the studied period. This corresponds to 7 meters in total for which we obtained an average MAPE score of 18.66%. For households that were vacant for some time, predictions turned out to be incoherent, some giving even negative values. 

Next steps: 
- For the classification, we could look at using more parameters to have a more insightful classification result.
- For the prediction, it seems that a time range of 6 months has its limits and it would be interesting to train the prediction model on a bigger timeframe to be able to extract patterns across the full year. We could also look at a method to obtain better predictions for properties that were partially vacant during the studied period. 


## Authors

- Sarah Sahli
- Daniel Gil


