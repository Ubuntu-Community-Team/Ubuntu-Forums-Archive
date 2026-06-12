---
title: "Apache 1.3 Problems"
date: 2005-12-20
forum: Desktop Environments
---

### Post by halflife28 on 2005-12-20
I compiled Apache from source, installed it, did all that good stuff, when I goto start the server, I get this message:

root@hiphopsource-servercpu:/usr/local/apache/bin # ./apachectl start
./apachectl: line 86: usr/local/apache/bin/httpd: No such file or directory
./apachectl start: httpd could not be started

Anyone know the solution to the problem i'm having?

Any would be appreciated, thanks!

---

### Post by Gandalf on 2005-12-20
why not using apache from repository?

---

### Post by halflife28 on 2005-12-20
It only has apache 2.0, I'm not too fond of that version, it doesn't play well with php the last time i've used it

---

### Post by Gandalf on 2005-12-20
Beleive me it does, apache2 is way too advanced compared to apache1, anyway rebuilding it will be a pain since u have to build apache with php and mysql support and build those two also (you can't install them from repo as they depend on the deb packages of apache, so go ahead with apache2 i say, unless u really insist, what have u used as --prefix while compiling?

---

### Post by halflife28 on 2005-12-20
/usr/bin/local, I followed through with the documentation on the Apache web site and everything went fine until I tried to start apache

PS, i'm not a linux guru, I'm a normal Windows user using ssh on my server.

---

### Post by halflife28 on 2005-12-20
I might as well go with apache2, whats the package name so I can use the apt-get command

---

### Post by Gandalf on 2005-12-20
[QUOTE=halflife28]/usr/bin/local, I followed through with the documentation on the Apache web site and everything went fine until I tried to start apache

PS, i'm not a linux guru, I'm a normal Windows user using ssh on my server.[/QUOTE]
no use /usr for that

as about apache2 do the following
```

sudo apt-get install apache2 php4 php4-mysql mysql-server libapache2-mod-php4

``` that would get u apache, php and mysql

---

