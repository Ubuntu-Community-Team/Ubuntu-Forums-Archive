---
title: "How to  connect JDBC in Ubuntu with OpenOffice database using MySQL"
date: 2009-02-09
forum: General Help
---

### Post by rlaknar on 2009-02-09
I am using Ubuntu 8.04.I would like to connect my Java program with OpenOffice database using JDBC or ODBC. I planned to use MySql base but I could not. Please help.

---

### Post by mistypotato on 2009-03-04
I'm working on a similar issue.

Trying to connect MSSQL JDBC driver to squirrel

If I come up with a solution, I'll post it

---

### Post by huam on 2009-03-15
Download java jdbc connector : [http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-3.1.14.tar.gz/from/http://mysql.mirrors.webazilla.nl/](http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-3.1.14.tar.gz/from/http://mysql.mirrors.webazilla.nl/)

In office program :
Choose 
extra -> Options -> OpenOffice.org -> Java 
Click Classpath.
Point to the jar file in the downloaded file :

mysql-connector-java-3.1.14-bin.jar

Than you can make a connection with your mysql database.

See also [https://help.ubuntu.com/community/UsingJavaDatabaseConnectivityAndOpenOffice](https://help.ubuntu.com/community/UsingJavaDatabaseConnectivityAndOpenOffice)

Also see (If you get a connection error)

[http://www.ubuntuforums.org/showthread.php?t=33601&highlight=java+mysql](http://www.ubuntuforums.org/showthread.php?t=33601&highlight=java+mysql)

---

### Post by AgentZ86 on 2009-03-24
> **huam said:**
> Download java jdbc connector : [http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-3.1.14.tar.gz/from/http://mysql.mirrors.webazilla.nl/](http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-3.1.14.tar.gz/from/http://mysql.mirrors.webazilla.nl/)

In office program :
Choose 
extra -> Options -> OpenOffice.org -> Java 
Click Classpath.
Point to the jar file in the downloaded file :

mysql-connector-java-3.1.14-bin.jar

Than you can make a connection with your mysql database.

See also [https://help.ubuntu.com/community/UsingJavaDatabaseConnectivityAndOpenOffice](https://help.ubuntu.com/community/UsingJavaDatabaseConnectivityAndOpenOffice)

Also see (If you get a connection error)

[http://www.ubuntuforums.org/showthread.php?t=33601&highlight=java+mysql](http://www.ubuntuforums.org/showthread.php?t=33601&highlight=java+mysql)

How do I know which version to download from the MySQL site ?

I see this link and it confuses me ?

[http://dev.mysql.com/doc/refman/5.1/en/connector-ooo-installation.html](http://dev.mysql.com/doc/refman/5.1/en/connector-ooo-installation.html)

Thanks again for the help this will be very useful

Please advise
Thanks

---

### Post by AgentZ86 on 2009-03-26
I have enabled local network access to msql and I cannot connect to mysql for some reason.

I'll keep trying and post back

---

### Post by cl333r on 2009-03-30
AFAIK by default MySQL doesn't open connections from other computers except localhost, unless configured to do so.

**mysql-connector-java-3.1.14-bin.jar** is too old, use 5.0 or 5.1 instead:
```
http://dev.mysql.com/downloads/connector/j/5.1.html
```

---

