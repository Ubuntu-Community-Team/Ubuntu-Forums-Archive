---
title: "HOWTO: Access a PostgreSQL database from within R"
date: 2007-11-16
forum: Education &amp; Science
---

### Post by Garyu on 2007-11-16
I recently wrote up how to access R from functions in a PostgreSQL database using the PL/R extension. Well, I tried doing it the other way, and that is possible too.

[http://help.nceas.ucsb.edu/index.php/R:_Data_input/output](http://help.nceas.ucsb.edu/index.php/R:_Data_input/output)
This page has a description for Dapper and Edgy, and the edgy version applies to Gutsy as well. Basically:

sudo apt-get install unixODBC odbc-postgresql

gksudo gedit /etc/odbcinst.ini
```
[PostgreSQL]
Description     = PostgreSQL driver for Linux & Windows
Driver          = /usr/lib/odbc/psqlodbcw.so
Setup           = /usr/lib/odbc/libodbcpsqlS.so
```

gksudo gedit /etc/odbc.ini
```
[ODBC Data Sources]
mydb1 = Database description

[mydb1]
Driver = /usr/lib/odbc/psqlodbcw.so
Database = your_dbname
Servername = localhost
Username = your_username
Password = your_password
Protocol = 8.2.5
ReadOnly = 0

[ODBC]
InstallDir = /usr/lib
```
This will make the ODBC connection available to everyone on the system. If you want user access only put this in ~/.odbc.ini. The "Protocol" is actually your PostgreSQL version.

[I]If you don't want to put username and password in this ini-file you can also provide it in your R code like so:
chan <- odbcConnect("mydb1", "your_username", "your_password", case="postgresql")[/I]

gksudo gedit /etc/postgresql/8.2/main/pg_hba.conf
```
local   your_db_name    your_username  trust
```
just add that to what is already there, don't remove anything.

sudo R
install.packages("RODBC")
q()

Now you should be able to access your database like this:
```
> library(RODBC)
> chan <- odbcConnect("mydb1", case="postgresql", believeNRows=FALSE)
> sqlTables(chan)  #List all tables in the DB
> mydata <- sqlFetch(chan, "some_table") #Return a table as a dataframe
> odbcClose(chan)

> chan <- odbcConnect("mydb1", case="postgresql", believeNRows=FALSE)
> sqlQuery(chan, "create table test (dummy text)")
> sqlQuery(chan, "insert into test 'hello world'")
> sqlQuery(chan, "select * from test")
> mydataframe <- sqlGetResults(chan)
> odbcClose(chan)

```


**[SIZE="4"]A better way of doing it...[/SIZE]**
...would have been to use RdbiPgSQL. But that is really hard to install in Ubuntu Gutsy as far as I have experienced.

[http://www.bioconductor.org/packages/2.0/bioc/html/RdbiPgSQL.html](http://www.bioconductor.org/packages/2.0/bioc/html/RdbiPgSQL.html)
This SHOULD work... after a few settings. But I haven't tried it all.

First of all you need to have the .h files from the postgresql-dev package. However, that is a dummy package without a candidate, so even
sudo aptitude install postgresql-dev
does nothing at all for you. You have do download the dev files and copy the includes manually!

Second of all, you have to set some paths:
```
export PG_LIB_DIR=/usr/lib/postgres/8.2/lib/
export PG_INCLUDE_DIR=/usr/lib/postgres/8.2/include/
```

And finally, 
sudo R
```
source("http://bioconductor.org/biocLite.R")
biocLite("RdbiPgSQL")
```

Let me know if you get RdbiPgSQL to work, because I never tried the copying .h files stuff as I just figured it was too much of a hazzle... So it is currently just a guess that this will work...

---

### Post by cottonmouth on 2007-12-25
Thank's for the writeup

Regarding the RdbiPgSQL:

1) You don't have to copy all the .h files:
```
aptitude install libpq-dev
```

2) You need to upgrade to gcc-4.2

3) The paths are somewhat different:
```
export PG_LIB_DIR=/usr/lib/postgresql/8.2/lib
export PG_INCLUDE_DIR=/usr/include/postgresql
```

4) Install through R as described above

5) Then from R
```

library(RdbiPgSQL)
conn <- dbConnect(PgSQL(), host="localhost", dbname="my_database", user="my_user", password="my_secret_password")
res <- dbSendQuery(conn, "select * from prices where item_id = 29")
mydata <- dbGetResult(res)

```

All the best.

---

### Post by IgyPiggy on 2012-05-10
There has been a change in where the psqlodbcw.so and libodbcpsqlS.so files are stored in Ubuntu 12.04 LTS. These files now resides in:

/usr/lib/x86_64-linux-gnu/odbc/  (for 64-bits version)
 
and 

/usr/lib/i386-linux-gnu/odbc/    (for 32-bits version)

---

### Post by overdrank on 2012-05-10
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

