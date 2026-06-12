---
title: "Ubuntu &amp; Web Services (Basic Question)"
date: 2006-09-13
forum: Desktop Environments
---

### Post by atraeyu on 2006-09-13
I just installed Ubuntu yesterday.  I'm trying to setup a development environment.  Installed Ubuntu desktop, now I'd like to get Apache/MySQL/PHP running on it.

I could just start installing packages with synaptic until I get it right, but I was hoping someone might know of a guide for a recomended way of doing this.

I believe Ubuntu has a package called "Lamp" that should be installed.  Is this correct?
Thanks!

---

### Post by Druidor on 2006-09-13
I know that lamp is installed & pre configure in the server version of Ubuntu but you can install them via synaptic or the apt-get install command on hte command line.

[http://www.ubuntu.com/server](http://www.ubuntu.com/server)  << For more information



Other more experienced inderviduals may be better suited to give advice on this but heres my few pennies worth.

**PHP Apache mysql install**
```

sudo apt-get install apache2 mysql-server mysql-client php4-mysql apache-common bittornado libapache2-mod-php4 libphp-adodb locales mysql-common php4-common pwgen

```



Also have a ganders at this help section 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by atraeyu on 2006-09-13
That definately makes sense.  I'll see if anyone else bites as this before I go and start installing those packages.  

All the web development before that I've done has been on a remotely hosted server - simply FTPing files to the server then running them remotely to debug & test.  Slow development process.

I'm hoping that there is a guide out there somewhere that will show me how to get apache/mysql/php (and later ruby on rails) up and running, and how to configure/use these services when they are running locally.

---

