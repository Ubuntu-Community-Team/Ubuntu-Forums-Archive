---
title: "problems with odbc"
date: 2006-07-06
forum: Desktop Environments
---

### Post by jonic on 2006-07-06
High everyone,

I've just installed Ubuntu (32bit) at work, switching from Windows :).
Everything works fine, except I have a problem with a MFC application, that I am running through wine. The application connects to a MySql server.
I've installed unixODBC, mysql drivers, and set up my data source with odbcConfig. The appplication can connect to the MySql server, however all the recordsets are opened in read-only mode. I use the same MySql user and password, from a windows machine and I don't have any problems.

Here are my odbc config files:
odbcinst.ini
```

[MySQL]
Description            = ODBC Driver for MySQL
Driver		          = /usr/lib/odbc/libmyodbc.so
Driver64		 = /usr/lib
Setup		         = /usr/lib/odbc/libodbcmyS.so
Setup64		        = /usr/lib
UsageCount	      = 100
CPTimeout	       = 
CPReuse		        = 

```

odbc.ini

```

[fasto]
Description		= MySQL
Driver		          = MySQL
Server		         = 192.168.1.1
Database	       = fasto
Port		          = 3306
Socket		        = 
Option		         = 
Stmt		         = 
User                     = ion
Password               = qwerisk7519

```

Does anyone have any hints to what might be causing this problem?

---

### Post by jonic on 2006-07-08
Any ideas? I am new to linux, so any help would be welcome. Are there some options that I should use in my unixODBC config files?

---

