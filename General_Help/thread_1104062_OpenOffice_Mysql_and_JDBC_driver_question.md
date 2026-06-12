---
title: "OpenOffice Mysql and JDBC driver question"
date: 2009-03-23
forum: General Help
---

### Post by AgentZ86 on 2009-03-23
Anyhow here is the additional topic/question:
I cannot seem to connect to the mysql database with OpenOffice
I have a webserver running mysql and php etc. but I'm only trying to connect to the database locally.
Using Ubuntu 8.04 32bit with OpenOffice 2.4

I have created a database table with myphpadmin on the server.
And I want to connect and create a form with OpenOffice.

When I go to OpenOffice menu/ Options/Java and select Class Path

I cannot seem to get a good test. when connecting to existing database.
When clicking on Add class path there is nothing in there, and I don't know what parameters to setup here. Even though the java version is shown in the previous screen.
I'm not sure what I'm doing wrong or where to start to diagnose this.

When I connect to existing database I select MySql, then Connect with JDBC, then it asks me what the database name is ? , then Server URL ?
then port number ? , then MySQL JDBC Driver class field?
Note-(com.mysql.jdbc.Driver)is in the JDBC Driver class field by default ?

When I click the test class button it says JDBC class driver could not be loaded. Although I did click to enable the driver for Mysql and JDBC which appears in the list as (Yes) and set to default 60 seconds inactivity ?

It's likely I'm doing something wrong, but I do not really know where to start diagnosing or if I've put in the proper parameters ?

Thanks again helping me figure this out.

---

### Post by Steve R. on 2009-10-31
I am having the same problem.  The Java runtime environment shows up as working under Options/Java. Version 1.6.0.  However, I don't know what to add for the JDBC Driver Class box to Access MySQL from Base??????

---

### Post by Steve R. on 2009-12-27
Well I blundered into the solution. See attached screen shot.

[Connect MySQL and Base]("http://wiki.services.openoffice.org/wiki/Connect_MySQLandBase")

---

### Post by AgentZ86 on 2009-12-28
I forgot that I solved this, but I wanted to post the solution so I created this doc on my server.

I hope this helps

[www.iclbiz.com/msql](www.iclbiz.com/msql)

---

