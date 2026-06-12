---
title: "ODBC Connection R and OpenOffice DB"
date: 2010-11-20
forum: Education &amp; Science
---

### Post by Axolotl9250 on 2010-11-20
Hi, When on Windows I used to create an ODBC for connection to R using RODBC, but since comming to Linux I haven't found out how to do this, although I have use RSQLite several times which is easier to connect, but not so much to edit the databases. Could anyone tell me how to set up an ODBC so I can connect other databases to R, not just SQLite?

Thanks,
Ben.

---

### Post by gunksta on 2010-11-21
By and large, ODBC is not commonly used in the world of Linux. ODBC is a Microsoft technology and it tends to work best on Microsoft systems. Setting up ODBC connections on linux is a pain. When I connect R to SQLite, I use RSQLite. To edit the database directly, the command-line tool sqlite3 is nice. Programs like sqliteman and sqlitebrowser may be more what you are looking for. It's a bit of a pain to set up, but I believe SQuirrelSQL is the best graphical SQL tool on any platform. It's a Java program and it's hosted on SourceForge. Download the generic version and put it in ~/bin. If you decide to use this and need some help setting it up, feel free to ask. The other two suggestions will be much easier to set up.

If you want to connect to other databases, look for the proper R library to connect directly, rather than go through ODBC. There are specific libraries for MySQL, Postgres, etc. Good stuff. I like SquirrelSQL because it can connect to all of these databases through JDBC and it provides a nice common interface to a variety of systems.

---

### Post by oldfred on 2010-11-22
Some info on ODBC.

see A neophyte's guide in 
[http://www.unixodbc.org/](http://www.unixodbc.org/)
Doing this as root will create and edit the /usr/local/etc/odbcinst.ini (for the driver info) and /usr/local/etc/odbc.ini (for the system DSN) files.

[http://www.easysoft.com/developer/interfaces/odbc/linux.html](http://www.easysoft.com/developer/interfaces/odbc/linux.html)
[http://www.easysoft.com/developer/interfaces/odbc/linux.html#dsn_install_unixodbc](http://www.easysoft.com/developer/interfaces/odbc/linux.html#dsn_install_unixodbc)


I tried doing one where I wanted to use ODBC to a MSaccess dB and it was pretty complex. Never worked, and I just converted it separately.

Downloaded from synaptic:
unixodbc-bin
unixodbc
libmyodbc

then I followed the instructions here to configure a odbc connection:

sudo apt-get install mdbtools
sudo ODBCConfig
ODBCConfig

For a different database but shows how to do ODBCConfig
[http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux](http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux)

---

### Post by jeenamenon on 2010-11-25
Take care of this point becomes great help , finish will take you to a Save dialog box to connect, use these settings to a file. This file you can use later to reconnect, instead of defining all the time.

---

### Post by gunksta on 2010-11-25
@oldfred - You can't use ODBC to connect to an Access database on Linux. Linux doesn't have the necessary systems to connect to an Access database. Access uses an embedded JET database, which only works on the Microsoft platform. There are a couple of JDBC drivers for Access but that's it.

---

