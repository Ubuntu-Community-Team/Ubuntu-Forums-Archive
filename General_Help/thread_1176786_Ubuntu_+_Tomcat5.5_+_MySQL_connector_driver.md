---
title: "Ubuntu + Tomcat5.5 + MySQL connector driver"
date: 2009-06-02
forum: General Help
---

### Post by marc.moonlight on 2009-06-02
Hello,
 
I've been spending the whole day on a CLASSPATH problem with my Tomcat5.5 install on ubuntu :
 
I've installed:
**apt-get install sun-java6-jdk sun-java6-jre tomcat5.5 libmysql-java**
 
I set : **TOMCAT5_SECURITY=no** 
in **/etc/default/tomcat5.5**
because of access right errors with Birt (the reporting tool I intend to run)
 
I expected the mysql-connector JAR driver installed thanks to **libmysql-java**, but I get the following trace in **catalina.log** :
**[COLOR=red]SEVERE: DriverClassLoader failed to load class: com.mysql.jdbc.Driver[/COLOR]**
**[COLOR=red]java.lang.ClassNotFoundException: com.mysql.jdbc.Driver[/COLOR]**
 
I'm pretty sure I didn't put the driver in the right folder, but I cannot figure out where to put it !
Wherever I put the mysql-connector JAR file, I get the same error.
 
If I look at the default installed driver, I see :
-rw-r--r-- 1 root root 679777 2008-07-31 14:53 **/usr/share/java/mysql-connector-java-5.1.6.jar**
lrwxrwxrwx 1 root root 30 2009-06-02 22:39 **/usr/share/java/mysql-connector-java.jar** -> mysql-connector-java-5.1.6.jar
 
Thanks in advance for your help,
 
Marc

---

