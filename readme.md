I imported my apache web server log, and parsed the data to receive a better dataframe layout, with each rows separated into individual columns
['host', 'timestamp', 'method', 'endpoint', 'protocol', 'status']

The result was a readable dataset with data filtered and sorted by date. There were no outliers.
+---------------+--------------------+------+-------------+--------+------+
|           host|           timestamp|method|     endpoint|protocol|status|
+---------------+--------------------+------+-------------+--------+------+
|  51.77.140.110|30/Aug/2020:06:25...|   GET|/wp-login.php|HTTP/1.1|   200|
|  51.77.140.110|30/Aug/2020:06:25...|  POST|/wp-login.php|HTTP/1.1|   200|
|  51.77.140.110|30/Aug/2020:06:25...|  POST|  /xmlrpc.php|HTTP/1.1|   200|
|  5.135.159.189|30/Aug/2020:06:48...|   GET|/wp-login.php|HTTP/1.1|   200|
|  5.135.159.189|30/Aug/2020:06:48...|  POST|/wp-login.php|HTTP/1.1|   200|
|  5.135.159.189|30/Aug/2020:06:48...|  POST|  /xmlrpc.php|HTTP/1.1|   200|
|192.241.225.120|30/Aug/2020:06:58...|   GET|            /|HTTP/1.1|   200|
| 106.38.241.168|30/Aug/2020:07:11...|   GET|            /|HTTP/1.1|   301|
| 138.197.174.39|30/Aug/2020:07:11...|   GET|            /|HTTP/1.1|   200|
| 138.197.174.39|30/Aug/2020:07:11...|   GET| /favicon.ico|HTTP/1.1|   404|
+---------------+--------------------+------+-------------+--------+------+

I dealt with missing values by first checking if there were any missing rows, and ran base_df.filter(base_df['value'].isNull()).count() which returned 0. If my results had null values, I would fill the missing values with logs_df = logs_df.na.fill()
