---
title: "openoffice2 odbc mysql (the pernial connection issue)"
date: 2005-12-22
forum: General Help
---

### Post by ninotob on 2005-12-22
I'm trying to connect openoffice2 and mysql through odbc.  I've done this before in the 1.x versions of openoffice without issue (redhat, suse, panther -- although that was technically neooffice).  I'm familiar with the "trail of tears" howto, and others.

I'm fairly confident that I have my obdc.ini and odbcinst.ini set up correctly -- I can sucuessfully use isql to test the odbc connection.  In openoffice, I've tried both wizards, the vanilla odbc and the mysql option.  Both fail with a message "can't connect to data source .... libodbc.so".  Note that I made a symbolic link to /usr/lib/libodbc.so.1 same location named "libodbc.so".  Didn't help.

I'm wondering if anyone has set up an odbc connection to mysql in openoffice2?  If so -- what's the magic?  I'm guessing that openoffice isn't looking in the right place for the odbc files -- where should I put them?

---

### Post by ninotob on 2005-12-22
I just installed openoffice 1.1 and that also fails.  So I must have bungled my odbc setup somehow.

When I try to browse my databses in the OO db setup utility, I get an error message stating "could not load program library libodbc.so.1 or it is corrupt".  I tried a reinstall of libmyodbc, unixodbc, and odbcinst1debian1, but that didn't solve my problem.

Is it of any significance that I'm running on an amd64 system -- something I read made me think perhaps it makes a difference, though in all the mad googling, I can't quite pin down what.

For reference:
cat /etc/odbc.ini
[test]
Description = test
Driver = MySQL
Server = localhost
Database = test
Port = 3306
Socket =
Option =
Stmt =

cat /etc/odbcinst.ini
[MySQL]
Description = ODBC Driver for MySQL
Driver = /usr/lib/odbc/libmyodbc.so
Setup = /usr/lib/odbc/libodbcmyS.so
FileUsate = 1
CPTimeout  =
CPReuse  =

And here is my isql output which suggests to me I should be good to go:
```

+---------------------------------------+
| Connected!                            |
|                                       |
| sql-statement                         |
| help [tablename]                      |
| quit                                  |
|                                       |
+---------------------------------------+
SQL> select version();
+----------------------------+
| version()                  |
+----------------------------+
| 4.0.24_Debian-10ubuntu2-log|
+----------------------------+
SQLRowCount returns 1
1 rows fetched
SQL>
```

---

### Post by ninotob on 2005-12-23
I just setup mysql and openoffice2 through ODBC on a 32 bit system from scratch.  Took 5 minutes and it worked just fine following the exact same steps as in my first post.  Both systems are up to date Breezy.

So I strongly suspect this has something to do with the amd64 version.

Anybody have any clues regarding where I should start troubleshooting??

---

### Post by ninotob on 2005-12-26
I deleted Breezy 64 and installed Breezy for i386.  No problem with openoffice/odbc/mysql.  I left some free space so I'm going to reinstall the amd-64 version there and try to get openoffice to connect through odbc as the first thing I do -- maybe I'd messed up my previous 64 install somehow.

Anyway, I'm still currious if any else has tried connecting openoffice through odbc to mysql in the amd64 Breezy distribution.

---

### Post by Mitush on 2006-05-17
Same story here... I've tried to set up odbc+mysql+oobase2 on amd64 breezy and got the "corrupted libodbc.so.1" messages, although isql works fine. Doing the same things on i386 worked out fine (i didn't even have to create the symbolic link libodbc.so). Looks like this might be a bug. A search for "libodbc" in bugzilla.ubuntu.com came out with nothing though.

---

### Post by mozkill on 2006-05-17
can someone create a WIKI howto for setting this up?  also, it would be nice to know how to setup odbc with something more difficult, such as a ORacel, DBase or Foxpro database...

if someone has the time and special knowledge, can you export the SQL Server Northwind database to a DBase format, move it to the Linux system, and then setup UNixODBC to connect to it and put the instructions for connecting to it in the WIKI?

---

