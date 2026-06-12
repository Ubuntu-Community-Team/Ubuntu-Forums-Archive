---
title: "problems connecting to MS SQL via FreeTDS"
date: 2009-06-03
forum: Desktop Environments
---

### Post by SpaceBas on 2009-06-03
Hey folks,
My google-fu may be weak, but I haven't been able to find anything that addresses this setup in much detail - let alone anything the covers problems. 

At work we have some proprietary software that uses MS SQL - nothing I can do about that. But I would like to start running Jaunty on my desktop full time. In order to do that, I need to be able to execute queries against those databases. I'm not much of a SQL expert, but understand the basic syntax of a SQL query. 

Through some tinkering and some great posts on this forum I have been able to setup FreeTDS and connect to our DBs (I think) but when I try and execute any queries, they fail miserably. The two query tools are isql (commandline) and OpenOffice Base.
isql returns errors (see below) and Base just locks up

/etc/freetds/freetds.conf
```
 cat /etc/freetds/freetds.conf 
#   $Id: freetds.conf,v 1.12 2007/12/25 06:02:36 jklowden Exp $
#
# This file is installed by FreeTDS if no file by the same 
# name is found in the installation directory.  
#
# For information about the layout of this file and its settings, 
# see the freetds.conf manpage "man freetds.conf".  

# Global settings are overridden by those in a database
# server specific section
[global]
        # TDS protocol version
;	tds version = 4.2

	# Whether to write a TDSDUMP file for diagnostic purposes
	# (setting this to /tmp is insecure on a multi-user system)
;	dump file = /tmp/freetds.log
;	debug flags = 0xffff

	# Command and connection timeouts
;	timeout = 10
;	connect timeout = 10
	
	# If you get out-of-memory errors, it may mean that your client
	# is trying to allocate a huge buffer for a TEXT field.  
	# Try setting 'text size' to a more reasonable limit 
	text size = 64512

# A typical Sybase server

# A typical Microsoft server
[DMC]
	host = 172.28.59.38
	port = 1433
	tds version = 7.0

```

/etc/odbcinst.ini
```
cat /etc/odbcinst.ini 
[FreeTDS]
Description     = TDS driver (Sybase/MS SQL)
Driver          = /usr/lib/odbc/libtdsodbc.so
Setup           = /usr/lib/odbc/libtdsS.so
CPTimeout       =
CPReuse         =
FileUsage       = 1

```

/etc/odbc.ini
```
administrator@bshsilinux1:~$ cat /etc/odbc.ini 
[ODBC Data Sources]

odbcname     = MyODBC 3.51 Driver DSN

[DMC]
Driver       = FreeTDS
Description  = CommuniCap - Dmc
Trace           = No
Servername      = DMC 
Database = MC_MAIN_DMC


```


Query code (which works all day long in SQL Manager on Windows):
```
cat ER\ IP\ level\ count.sql 
SELECT COUNT(DISTINCT Mc_UbClm.Clm_Id) AS QL_Cnt
FROM Mc_UbClm
	INNER JOIN Mc_UbSvc
		ON Mc_UbClm.Clm_Id = Mc_UbSvc.Clm_Id
WHERE Mc_UbClm.Er_Clm_Ind = 1
AND Mc_UbClm.Out_Pat_Clm_Ind = 0
AND Mc_UbClm.Statement_From BETWEEN '2007/09/01' AND '2008/08/31'
AND Mc_UbSvc.Proc_Code = '99283'
```

Command
```
cat ~/SQL/'ER IP level count.sql'  | isql DMC 'CommuniCap - DMC' -verbose
```

Result:
```
at ~/SQL/'ER IP level count.sql'  | isql DMC 'CommuniCap - DMC' -verbose
+---------------------------------------+
| Connected!                            |
|                                       |
| sql-statement                         |
| help [tablename]                      |
| quit                                  |
|                                       |
+---------------------------------------+
SQL> [37000][unixODBC][FreeTDS][SQL Server]Statement(s) could not be prepared.
[37000][unixODBC][FreeTDS][SQL Server]The multi-part identifier "Mc_UbClm.Clm_Id" could not be bound.
[ISQL]ERROR: Could not SQLPrepare
SQL> [37000][unixODBC][FreeTDS][SQL Server]Incorrect syntax near the keyword 'FROM'.
[37000][unixODBC][FreeTDS][SQL Server]Statement(s) could not be prepared.
[ISQL]ERROR: Could not SQLPrepare
SQL> [37000][unixODBC][FreeTDS][SQL Server]Incorrect syntax near the keyword 'INNER'.
[37000][unixODBC][FreeTDS][SQL Server]Statement(s) could not be prepared.
[ISQL]ERROR: Could not SQLPrepare
SQL> 

```
Those errors continue for several more lines...

So - anyone have any ideas? Something I may be missing?

Thanks so much in advance! 
-N

---

### Post by jonobr on 2009-06-03
no takers on this one eh:-(
I was hoping to see a response.


I was having a dickens of a time trying to get a client to work with a Mssql db,
I ended up using sqsh which is in synaptic.
It uses the freetds stuff, but I dont recall running into the issues you saw,

I may try setting this up again to see whats up.

Sqsh wasnt the best for interacting with your Db but I found options were limited

---

### Post by SpaceBas on 2009-06-04
> **jonobr said:**
> no takers on this one eh:-(
I was hoping to see a response.


I was having a dickens of a time trying to get a client to work with a Mssql db,
I ended up using sqsh which is in synaptic.
It uses the freetds stuff, but I dont recall running into the issues you saw,

I may try setting this up again to see whats up.

Sqsh wasnt the best for interacting with your Db but I found options were limited

Thanks jonobr - I'll give sqsh a try and see what happens... the good news is that we do read-only work, so as long as I can run a query and get a report, I will be fine.

The challenge is that since both isql and Base did not work, I suspect its at a lower level...

---

### Post by jonobr on 2009-06-04
I would be inclined to agree!


Also, just to lower the bar for you,
dont expect a lot out of sqsh

its single line entry and then a go at the end, its a bit clunky but hopefully it will be good for you

---

### Post by jonobr on 2009-06-05
Hey SpaceBas

I went ahead and resintalled sqsh to see if I ran into the problems you had and It appears things are going ok for me. (It was a while since used sqsh)

Heres what I did,
I went to synaptic
and marked sqsh for installation, 
It also installs FreeTDS as one of its dependencies.


When It installed I connected using the command line.
I did this from the default install.

```
sqsh -S <ipaddress of Sql db> -U <myusername> -P <mypassword>

1\ select * from mydb.dbo.mytable where itemvalue = '3'
2\go
```

This all worked.

Im connecting to a regular win2005 MSSQl DB.
The only thing I noticed is that I could not use my windows authentication and had to use my sa pw although I guess there is some config that gets that info for you

Also. if you man sqsh or go to the sqsh web page you can find the manual which gives a lot of better details if you want to get all fancy shmansy on the things you want to do:p

Best of Luck!!

---

### Post by jonobr on 2009-06-05
Im starting to relearn this again :-)

One thing you should note and will be of use to you,
When you enter your SQL query on the first line,
at the second line where you enter go, you can do typical piping and redirecting such as

```
\go | more
\go >myfile.txt

go | grep xxxx
```

etc

---

