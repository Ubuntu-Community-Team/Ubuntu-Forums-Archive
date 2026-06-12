---
title: "Problems after 'manually' upgrading PHP"
date: 2006-08-27
forum: Desktop Environments
---

### Post by grav on 2006-08-27
I had problems with the version of PHP which comes with Dapper (5.1.2 - the DOM-classes didn't work well), so I found version 5.1.4 and all the dependencies from the Edgy Eft dist and installed them with dpkg.

Everything worked fine. However, after using apt-get update, the packages for supporting MySQL has been uninstalled, and I am not able to install them. The problem is that php5-mysql depends on php5-mysqli and vice versa. How do I come around this?

Regards, Mikkel

---

### Post by grav on 2006-08-27
I solved it myself by using 

sudo dpkg -i php5-mysql_5.1.4-0.1ubuntu1_i386.deb php5-mysqli_5.1.4-0.1ubuntu1_i386.deb

---

