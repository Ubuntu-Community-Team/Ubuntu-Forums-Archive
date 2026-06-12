---
title: "Ubuntu SQL server - what now?"
date: 2009-05-16
forum: General Help
---

### Post by ubila on 2009-05-16
Hi all :)
Im very new to ubuntu but im trying to replicate my work enviroment at home, to the same as i have at work!
 
I have successfuly set up ubuntu server following this guide (so far loving it!)[http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10)
 
At work i use SQLyog to connect / edit / create databases, it seems that i need to purchase this though ?
 
Is there any other way of managing databases? Maybe someone knows a tutorial or guide that ive missed?
 
Any help would be appreciated :) 
 
Cheers!!!

---

### Post by LoneWolfJack on 2009-05-16
check out phpmyadmin, it's probably the default management console for 90% of the mysql people out there
[http://www.phpmyadmin.net/]("http://www.phpmyadmin.net/")

---

### Post by mbeach on 2009-05-16
> **ubila said:**
> 
Is there any other way of managing databases? Maybe someone knows a tutorial or guide that ive missed?


Depending on which database you are using, typically there is a manager for each. 

For example mysql has the query browser and admin tools:
[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)
also available in the repositories as packages:
mysql-admin
mysql-query-browser

Install using your preferred method.
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Postgresql also has a tool called "pgadmin3"
[http://www.pgadmin.org/](http://www.pgadmin.org/)

You could also use generic tools like dbvisualizer but need to obtain the drivers for your particular database.
[http://www.minq.se/products/dbvis/](http://www.minq.se/products/dbvis/)
[http://www.minq.se/products/dbvis/doc/drivers.jsp](http://www.minq.se/products/dbvis/doc/drivers.jsp)

and then there are the web based tools like phpmyadmin.  It is probably also a good idea to have a basic understanding of the native clients (from the command line) for those times when you are in a pickle.
[http://dev.mysql.com/doc/refman/5.1/en/mysql.html](http://dev.mysql.com/doc/refman/5.1/en/mysql.html)

---

### Post by ubila on 2009-05-20
Thanks heaps - Very helpful :)

---

