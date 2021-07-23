# World Weather Analysis with Python APIs

## Project Overview
The purpose of this project was to gather website data using API (Application Programming Interface) to identify potential travel destinations and nearby hotels across the globe. CitiPy module was used to identify cities while OpenWeatherMap and Google Maps API were used to get weather and hotel information respectively. Based on specific weather criteria, a new Pandas DataFrame was created, used to make a travel itinerary by requesting data from Google Directions API, and created maps with marker layers through gmaps.

### Resources
- Data:
    - [WeatherPy_Database](https://github.com/samanthajpv/World_Weather_Analysis/blob/a3b09720de0e6ce98e7190b2d010be4d5109be55/Weather_Database/WeatherPy_Database.csv) - retrieved on July 21, 2021, contains weather information for all identified cities
    - [WeatherPy_Vacation](https://github.com/samanthajpv/World_Weather_Analysis/blob/a3b09720de0e6ce98e7190b2d010be4d5109be55/Vacation_Search/WeatherPy_vacation.csv) - contains hotel names and data filtered to the entered weather criteria
- Code:
    - [Weather_Database](https://github.com/samanthajpv/World_Weather_Analysis/blob/a3b09720de0e6ce98e7190b2d010be4d5109be55/Weather_Database/Weather_Database.ipynb)
    - [Vacation_Search](https://github.com/samanthajpv/World_Weather_Analysis/blob/a3b09720de0e6ce98e7190b2d010be4d5109be55/Vacation_Search/Vacation_Search.ipynb)
    - [Vacation_Itinerary](https://github.com/samanthajpv/World_Weather_Analysis/blob/a3b09720de0e6ce98e7190b2d010be4d5109be55/Vacation_Itinerary/Vacation_Itinerary.ipynb)
    
- Software: Jupyter Notebook 6.3.0
- Language: Python 3.7.10
    - Dependencies: 
        - citipy
        - numpy
        - pandas
        - requests
        - gmaps 
- API (documentation):
    - [OpenWeatherMap](https://openweathermap.org/api)
    - [Google Maps Platform](https://developers.google.com/maps)

## Method

### Weather Database
A set of random latitude and longitude combinations were generated using the ```np.random.uniform()``` method. With the CitiPy module, the nearest city to the coordinates was identified. The OpenWeatherMap API call was made to request weather information on the cities where data was returned in JSON (JavaScript Object Notation) format. Information gathered was transformed into a Pandas DataFrame (see image below) and exported as a csv file.
<p align="center">
    <img src="https://github.com/samanthajpv/World_Weather_Analysis/blob/90127fe95f78bc29c00ef261cbce144a2d3486de/Additional/Weather_Database.png" width="600" height="275" align="center">
    <h5 align="center">Weather DataFrame</h5>
</p>

### Vacation Search
Input statements were created to prompt the user to enter desired minimum and maximum temperature criteria for their vacation search. For the data moving forward, temperature range entered was 75-90F. From the WeatherPy_Database file, a new DataFrame was created with only the cities that fall under the temperature criteria. DataFrame was checked for empty rows before creating the DataFrame with the column for the hotel names. 

Google Maps API - Nearby Search request was made with the parameters latitude and longitude as location, the type "lodging", and a specified radius. From the JSON formatted data, hotel names were added to the DataFrame (see image below). Rows were dropped for cities where no nearby hotel was found and clean DataFrame was exported as a csv file.
<p align="center">
    <img src="https://github.com/samanthajpv/World_Weather_Analysis/blob/90127fe95f78bc29c00ef261cbce144a2d3486de/Additional/Vacation_Search.png" width="600" height="275" align="center">
    <h5 align="center">Weather DataFrame with Hotel Information</h5>
</p>

With the use of gmaps, a marker layer map was created with pop-up markers for each city. The info box contains the hotel name, city, country, and weather information.
<p align="center">
    <img src="https://github.com/samanthajpv/World_Weather_Analysis/blob/a3b09720de0e6ce98e7190b2d010be4d5109be55/Vacation_Search/WeatherPy_vacation_map.png" width="700" height="280" align="center">
    <h5 align="center">Google Map with Pop-Up Marker for Each City</h5>
</p>

### Vacation Itinerary
From the WeatherPy_Vacation file, four cities were selected as the possible travel route where a separate DataFrame was created for each city. The ```to_numpy()``` function was used to get the city coordinates as tuples for the creation of a direction layer map as seen below.
<p align="center">
    <img src="https://github.com/samanthajpv/World_Weather_Analysis/blob/a3b09720de0e6ce98e7190b2d010be4d5109be55/Vacation_Itinerary/WeatherPy_travel_map.png" width="700" height="400" align="center">
    <h5 align="center">Google Map of Travel Route</h5>
</p>

The four separate DataFrames were then combined using the ```concat()``` function. This was used to create the marker layer map of the cities on the travel route.
<p align="center">
    <img src="https://github.com/samanthajpv/World_Weather_Analysis/blob/a3b09720de0e6ce98e7190b2d010be4d5109be55/Vacation_Itinerary/WeatherPy_travel_map_markers.png" width="700" height="400" align="center">
    <h5 align="center">Google Map of Travel Destinations with Hotel Information</h5>
</p>

## References
(1) Trilogy Education Services. (2021, July). *Module 5 Challenge*. https://courses.bootcampspot.com/courses/626/assignments/13386?module_item_id=212505

(2) cs95. (2020, January 7). Answer on the online question post *Convert a dataframe to list of tuples duplicate*. Stack Overflow. Retrieved on July 21, 2021 from https://stackoverflow.com/questions/45285244/convert-a-dataframe-to-list-of-tuples
