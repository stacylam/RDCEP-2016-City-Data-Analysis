# RDCEP-2016-City-Data-Analysis

#Finding Midpoints of City Data Street Segments

For every street surveyed in the summer of 2015, I used http://www.geomidpoint.com/ to locate the midpoint. Within the dataset located in Google drive, the street segment: Granville/Keystone --> Dead end was not included because the location could not be found. Also, the street segment: Rosehill/Paulina --> Rosehill/Ashland was duplicated which I then deleted one.

#Google Heat Maps API Javascript
In order to use Google API, you must create a API Key https://developers.google.com/maps/documentation/javascript/get-api-key
The first heat map called Heat Map Template is a map of San Francisco and instructions can be found https://developers.google.com/maps/documentation/javascript/examples/layer-heatmap (Remember to insert your API KEY)
The locations on the template only show the points and have no weighted value. 

The file Chicago Heat Map (No Weighted Values): Has the midpoint street segment locations and has comments on the start and end date of each survey. However, the locations do not have weighted values associated to each point. 

The file Chicago Template of Weight Values: include the location of each street surveyed and has a template of how to input weighted values. This file allows you to copy and paste your own values. 

The file Sum of Security Signs (Weighted): Has included the dissipate function which allows the data to be accurately presented when a user zooms in. Also has the maxIntensity function and can be set accordingly. This file has included the weighted values on the Sum of Security signs that is associated to each street segment surveyed. The sum of the security signs was calculated in Google Sheets. It is the sum of Neighborhood Watch Signs, We Call Police, No Tresspassing, Dog Sign, and Alarm Systems. Note: The data for No Trespassing, Dog Sign, and Alarm Systems were only surveyed for the second half of the summer. Therefore, there is no data for half of the streets surveyed and was considered NULL. (In google sheets, the value NULL was considered 0). 

The file Alarm Systems (Weighted): Since Alarm Systems contain NULL values, it was assigned as -1. As a result, the NULL values showed as red blocks on the heatmap. However, this may be misleading to the users because the heat map color scale has two settings and can be toggled from green to red and from blue to red. This may be a potential problem because a user can mistake NULL values as neighborhoods with a greater amount of Alarm System signs. 

The File Tree Debris Heat Map: Shows the points with weighted value, but when a user zooms out, the information is inaccurate because the points that show a greater density are also red. The data should only represent areas with a high amount of tree debris and not the density of points. 

The file Search Box Function: Has included the function of allowing the user to search and area and it would then zoom into that area. However, no points has been able to show up. 

The file Heat Map with Json Test: With the help of Raffaele Montella, this heat map has been able to process the data in a json file. Instead of inputting the data manually, the google sheet data can exported as a json file and is used to extract values. Instructions can be found http://blog.pamelafox.org/2013/06/exporting-google-spreadsheet-as-json.html. 

#QGIS Thematic Map (Mapping Our City data (Block segments) and Census data (Block Groups)

Shape files can be found here:
http://www.cityofchicago.org/city/en/depts/doit/dataset/boundaries_-_censusblocks.html  <-- Chicago street blocks
https://www.census.gov/geo/maps-data/data/cbf/cbf_blkgrp.html  <-- Illinois Block Groups 

Census Data Source: http://factfinder.census.gov/faces/nav/jsf/pages/index.xhtml  <-- In QGIS, used estiamte amount of people who speak English

Issue: Our City Data that was surveyed contains midpoint locations of streets (Blocks), but the census provides data in Block Groups. In addition, the census data does not provide a polygon of the block groups. In order to map the data, the GEOID of the blocks and Block Groups need to be matched. 

Solution: Raffaele Montella has written a code that says if a point is contained within a polygon, then the point belongs in that polygon. Therefore, points contained in a block segment was color coded to indicate whether that block segment was in Block Group 1-7. As a result, the code creates an output csv that contains the GEOID of the CENSUS, Polygon Geometry of Chicago Block Groups, and the Value (in this case, it is the amount of people who can speak English). This code allows users to visualize the city in Group Blocks that ranges from 1-7 as well as compare the summer city data to the census data. 







  
