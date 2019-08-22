# Project Outline

## Project Demo Video:

Project Pitch (1 Min): https://www.youtube.com/watch?v=0KqPo5OysVM
Project Demo (6 Min): https://www.youtube.com/watch?v=o6eGbKIQbAg

## Overview

Increasing production of various types of aircrafts worldwide (i.e. Boeing, Airbus) and expanding flight routes for airlines put heavy pressure on the operation teams of each airline. In particular, airlines face fierce competition so that it is of their best interests to utilize best practices to reduce unnecessary costs. To achieve the cost reduction, airlines typically want to maximize the utility of airplanes and use minimum number of planes to satisfy customer needs. One important problem that every airline has to address is the fleet assignment problem: assigning aircrafts to available routes. **Given a flight schedule and set of aircrafts, the airlines will have to determine which type of aircraft should fly each flight segment and find an optimal assignment solution to minimize cost.**

Despite having cost management experts, operation teams from airline companies often find it difficult to tackle this optimization problem. Fleet assignment varies from week to week or even day to day, that is, airlines reassign their aircrafts frequently in order to take into account of seasonality and special situations (like holidays, weekends). Moreover, there is a list of complicated factors associated to assigning a fleet to a flight leg that will be demonstrated in the later part. The key solution requires a comprehensive model that encompasses all of these variabilities and provides an optimal solution in every situation. Furthermore, the model should visualize the cause-and-effect relationship between any selected aircraft type and the associated cost incurred.
In this project, we take the perspective of a small airline whose profit relies heavily on the effective assignment of limited aircrafts to available routes. Small companies have a fewer number of routes, thereby reducing the total number of variables and making the problem more solvable using excel. The problem includes two major steps. The first step is to forecast demand for each route. Demand is a major variable for the fleet assignment problem. Unlike other fixed variables like flight distance or seat capacity, demand varies from week to week and depends on things like time of the year, days of the week, competitor prices, own ticket prices, and etc. Forecasting demand is crucial and everything else should be calculated based on forecasted demand. The second step is to optimize aircraft routing assignment. This step takes into account of other factors like demand and find an optimal type and number of aircrafts for each existing route. We will compare our solution to the airline’s existing assignment and find out if there is anything the airline can change or improve.
     
This project takes the form of a  workbook-based dashboard with embedded tables and graphs (Format A) . It incorporates variability in an  optimization search mechanism (Route 1) . We will use visuals to demonstrate our calculating process and results to provide clarity to make the whole process more user -friendly.

## Intended Use

This model takes the perspective of a small airline with manageable amount of routes and aircrafts. However, this model also intends to help operation managers from any airline company to optimally allocate different types of aircrafts to designated routes. The model will allow airline companies to generate optimal flight assignment every single day of the year and is guaranteed to minimize cost while satisfying customer needs. Airline companies can visualize the individual cost of having the particular type of airplane associated to the routes as well as the total cost. They can also alter the model by changing the number of planes, plane types, adding or reducing routes and providing other customer services. The model should be a base case model for companies that want to seek changes or conduct sensitivity analysis.

## Key Factors and Dependencies

*[N] as numerical, [C] as categorical:*

### Key factors on demand forecasting:

##### Dependent variable:

- [N]Past data on ticket demand: Data from the past 5 years

##### A list of independent variables:

- [C]Days of the week: Weekdays or weekends;
- [C]Time of the year: Effect of different quarters (Q1, Q2, Q3,Q4);
- [N]Competitor price: Comparison of competitors’ ticket price to our own price on each route;
- [N]Own ticket prices: Ticket prices by different classes (firstclass, business class, economic class);
- [C]Source of purchasing tickets: Official website vs. ticketsales agencies (price discounts)

Relationship between factors and output: ample past data will be collected regarding each factor and a regression model will be utilized to generate a reliable forecast taking into account of all factors and data.

### Key factors on fleet assignment:

##### Key factors on routes:

- [C]Time availability (Operating time and takeoff/landing time availability in airports);
- Attributes of departure and arrival airports ([N]Runway length, [C]Pavement Classification, [C]ILS Category, [C]maintenance availability, [C]catering availability, [N]air traffic volume, [C]lounge availability);
- [N]Length (Over land and over water, alternate aerodrome distance);
- [C]Special operation requirement (RVSM requirement for high capacity areas , ETOPS requirement for over water operation, Polar operations requirement, Reclear requirement);
- [N]Demand (premium seats and economy seats);
- [C]Cabin requirement (Onboard wifi, flatbed seats); 

##### Key attributes of aircraft:

- [C]Status (location, inflight / on the ground, operability);
- [N]Air range;
- [N]Capacity (Premium cabin seating, Economy cabin seating, Cargo);
- [N]Fuel economies;
- [N]Maintenance cost and [C]maintenance schedule;
- [N]Passenger consumption expenses (Catering, beverage, blankets, etc);
- [N]Crew requirement (to compute crew cost);
- [C]Cabin amenities (flatbed, onboard wifi, inflight entertainment);
- [C]Airworthiness (ESTOP certification, fuel capacity, FAA directives, etc.)

Key factors on routes can be extracted from flight charts and factors regarding airports can be extracted airport specifications. Demand will be derived from demand forecasts in the earlier part of this model. Cabin requirement can be drawn from common knowledge (i.e. long haul flights needs flatbed and personal entertainment). Special operation requirement is only applicable to certain routes such as polar routes (usually for flights among Aisa, North America and Europe), flights over water and flights in high-capacity airspace (such as North Atlantic).
Most of the key factors on aircraft depend on aircraft type, which can be easily extracted from aircraft specifications. Other information can be extracted from airlines that operate these aircrafts.

## Limitations

The purpose of this model is to help airline with optimal aircraft assignment in the context of real world application. Potential limitation is anything that happens in the real world that is not taken into account or accurately predicted by the model. These things include:

##### Complicated actual flight routes especially for large airlines, such as:
- Flights involving multiple transits (for boarding and reloading);
- Flights involving technical stops (usually for refueling);
- Complicated air traffic control requirements, which usually leads to
delays and alternate landings;

##### Certain inevitable events are not taken into consideration, such as:
- Special weather conditions that will influence operation such as storms, fog, severe icing condition, volcanic activities, and etc.;
- Emergencies such as onboard fires, terrorist attacks, bird strikes, engine failures, and etc.;
- Political factors such as regional political instability, denied entry to airspace of certain countries and freedom of the air, and etc.;
- Regulatory limits such as FAA grounding orders, and etc.;

##### Other factors affecting demand including: recent trends, technological innovation, changes in consumer tastes.


## Draft of Analytics

##### Model Construction Stage 1: Forecasting Demand

Step 1 Utilize online database such as Statista and Data Center to search for past data on ticket demand, own ticket prices, competitor prices and seasonality (Q1 - Q4, days of the week), length of routes, cabin requirements, and etc. We plan to extract data from the past 5 years as these data are not too outdated and can provide enough references.
Step 2 Manipulate data on an excel spreadsheet by using regression to forecast demand. We plan to use all of these factors as inputs and demand as the output.
Step 3 Interpret regression output such as P-value and adjusted R-square and modify the model based on P-values of each coefficient (Take out variables with p-value less than 0.05 and add variables so that the adjusted R-square can be as large as possible).
Step 4 After determining the best regression equation, we will forecast future demand for the particular route. Use this method for every available route to obtain forecasted demand associated to each route.

##### Model Construction Stage 2: Fleet Assignment Optimization

Objective: minimize total cost
Decision Variables: aircraft type and number of aircrafts assigned to operate each route
Constraints: The aircraft assigned to each route should meet limitations and requirements of the route (see a detailed list of key factors on fleet assignment above). At the meantime, the aircraft assigned to this route cannot be assigned to another route at the same time, nor can it be in maintenance or be in locations other than the departure airport. The aircraft should not be operated under nonpermissible weather conditions. As well, the airline needs to follow the maintenance schedule and FAA regulations regarding a specific type of aircraft.