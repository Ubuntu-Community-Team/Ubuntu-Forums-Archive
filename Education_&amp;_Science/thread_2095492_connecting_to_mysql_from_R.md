---
title: "connecting to mysql from R"
date: 2012-12-17
forum: Education &amp; Science
---

### Post by bistro on 2012-12-17
Hello

I've just installed R for the first time, along with DBI, Rmysql packages - all from package manager (using Kubuntu at the moment).

I can't connect to mysql:

```

con1 <-dbConnect(MYSQL(), user="myname", password="mypassword", host="localhost", dbname="casualty")

 error in evaluating the argument 'drv' in selecting a method for function 'dbConnect': Error: could not find function "mysql"

```

mysql is running. Is this this to do with the location of specific files?

Many thanks

Dave

---

### Post by bistro on 2012-12-21
Update in case it's useful for anyone.

1. Given up on Rmysql for now, as everything I turned up in searches indicates it's a little problematic for linux.
2. But did successfully connect through RJDBC driver (ref [here]("http://www.rforge.net/RJDBC/")).

Install libmysql-java from kubuntu package manager.
Have DBI and RJDBC packages installed in R.
Then
```

drv <- JDBC("com.mysql.jdbc.Driver", "/usr/share/java/mysql-connector-java-5.1.16.jar", identifier.quote="`")
 conn <- dbConnect(drv, "jdbc:mysql://localhost/mydbname", "myusername", "mypassword")

```

---

