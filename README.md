# Rail-road-planing-SQL
# Objective:
In this project we analysed flight data for 10 years (2008 to 2017) to plan buliding a high-speen rail road 
tunnel between two airports that have high air trafic and long arrival delay. 
1) The distance between the two airports must be between 300 to 400 miles.
2) The two airports must have average at least 5,000 flights per year between them, in each direction.
3) Among the pairs, identify the one pair that has the largest total number of seats on the palines that flew between them.
4) Report the arrival delay for the flights between these two airpots (it can justify buliding a rail road)


# SQL select statement (run in Impala)
SELECT f.origin,f.dest,round(sum(flight)/10) AS anual_flights,
avg(arr_delay) AS avg_delay,
round(sum(p.seats)/10) AS annula_capacity
FROM fly.flights as f LEFT OUTER JOIN fly.planes as p ON f.tailnum=p.tailnum
WHERE distance between 300 AND 400
GROUP BY f.origin,f.dest having anual_flights >=50000
ORDER BY sum(p.seats) DESC;


