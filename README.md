# PyBer_Analysis

## Overview of the Analysis

The purpose of this analysis was to create a DataFrame of the ride-sharing data and summarize it through the type of city. A line graph was then made using a resampled version of the DataFrame to properly chart all three city types. The intitial ride-sharing data was provided for in the [city_data.csv](https://github.com/stwpf01/PyBer_Analysis/blob/main/Resources/city_data.csv) Series and the [ride_data.csv](https://github.com/stwpf01/PyBer_Analysis/blob/main/Resources/ride_data.csv) Series. These were then merged into one DataFrame on the city column since that was shared across the two Series. The script of code can be found in the [PyBer_Challenge.ipynd](https://github.com/stwpf01/PyBer_Analysis/blob/main/PyBer_Challenge.ipynb) file and the results of the analysis will be detailed below in the "Results" section.
## Results

Here are the results for the Total Ride, Total Drivers, Total Fares, Average Fare per Ride, and Average Fare per Driver per city type:

![Summary_DataFrame](https://github.com/stwpf01/PyBer_Analysis/blob/main/analysis/Summary_DataFrame.png)

Here is an example of how this information was found; To get the Average Fare per Ride is as follows:

1. A variable was created to find the total rides. This variable was equal to the merged DataFrame using the groupby function on type (a column in the DataFrame) and then the count function on the ride_id (another column in the DataFrame). This means that it sorted through the DataFrame through the type column via the values of said column, then counted them through the ride_id column. The count function was used instead of the sum function because the amount of rides was needed, not the sum total of the rides. While the ride_id column was used, using the count function on any of the other columns would've given the same result since there were no null values.
(`total_rides = pyber_data_df.groupby(["type"]).count()["ride_id"]`)

2. A similar line of code was made to find the total fares per city type. This code, however, did use the sum function because the total sum of the fares per city type was needed, not how many fares there were in total.
(`total_fare = pyber_data_df.groupby(["type"]).sum()["fare"]`)

3. The average fare per ride was found by dividing the results of the total fare variable from the total rides variable.
(`avg_fare_ride = total_fare / total_rides`)

These results were placed into a line graph as seen below:

![PyBer_fare_summary](https://github.com/stwpf01/PyBer_Analysis/blob/main/analysis/PyBer_fare_summary.png)


Based on the line graph and the summary of the DataFrame, Urban cities made much more in terms of total fares compared to the Rural and Suburban cities. Furthermore, because there are significantly more drivers compared to the number of rides, the average cost of a ride is lower in Urban cities, but also the amount of fare a driver makes is much less when compared to the Rural and Suburban cities.

## Summary


If one was to become a driver at the PyBer company, it would be more beneficial to be employed in a Rural or Suburban area since they make more than a driver in an Urban city. This could be mitigated somewhat if those drivers in Urban city were paid more per ride compared to their counterparts in Rural and Suburban cities. This could be justified by pointing out that there are more than double the amount of rides compared to Suburban cities and more than thirteen times the amount of rides compared to Rural cities. Another recommendation would perhaps be hiring more people for Rural and Suburban cities, and also changing the amount per ride to lower the cost of the average ride to make it more affordable for the customer.
