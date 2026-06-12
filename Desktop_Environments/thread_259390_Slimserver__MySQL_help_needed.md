---
title: "Slimserver / MySQL help needed"
date: 2006-09-17
forum: Desktop Environments
---

### Post by citizenkeith on 2006-09-17
I installed Slimserver via apt-get:
[http://wiki.slimdevices.com/index.cgi?DebianPackage](http://wiki.slimdevices.com/index.cgi?DebianPackage)

Now when I start it up, I get the following errors:

```
keith@keith-desktop:~$ slimserver
060917 10:18:43 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
060917 10:18:43 [ERROR] Do you already have another mysqld server running on port: 9092 ?
060917 10:18:43 [ERROR] Aborting

060917 10:18:43 [Note] /usr/sbin/mysqld: Shutdown complete

2006-09-17 10:19:12.9659 ERROR: MySQLHelper: createSystemTables() Couldn't connect to database: [Can't connect to local MySQL server through socket '/home/keith/Cache/slimserver-mysql.sock' (2)]

```

I was using MySQL for Amarok, but switched it over to SQLite. I guess MySQL is still running... but I'm not sure what to do. Any advice or links would be appreciated. :)

---

