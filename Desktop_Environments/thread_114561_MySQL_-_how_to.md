---
title: "MySQL - how to ???"
date: 2006-01-08
forum: Desktop Environments
---

### Post by tatacalu on 2006-01-08
oi there !!!

I installed mysql on Ubuntu... but I really don't know where to start... where can I find it? what program should I start to controle the database server? in windows there is a graphical user interface for mysql, is there a version of it for Linux?

any ideea would be welcomed because I really don't know how to operate mysql on linux.

should I install aditional packages?
PHPMyAdmin is good in this sittuation ? I mean, can I acces everything I need through it?

Thanks' :eek:

---

### Post by lnostdal on 2006-01-08
Found this: [http://www.mysql.com/products/tools/administrator/](http://www.mysql.com/products/tools/administrator/)

(I'm guessing the package is named mysql-admin)

I mosty use PostgreSQL, so my answer might not be the "defacto standard" for what MySQL-users use.

Edit:
Oh, and you start/stop/etc. MySQL by doing sudo /etc/init.d/mysql start

---

### Post by tatacalu on 2006-01-08
ok, I entered the download page:

[http://dev.mysql.com/downloads/administrator/1.1.html](http://dev.mysql.com/downloads/administrator/1.1.html)

what package would you recommend (from the linux ones, of course heheh) so I can install it in the easiest way ?

---

### Post by lnostdal on 2006-01-08
I'd try using Synaptic in Ubuntu to install the package named mysql-admin before doing that!

In the menu; System -> Administration -> Synaptic Package Manager

edit:
Always try to use the package manager included with your Linux distro before trying to install "general" packages.

---

### Post by spartas on 2006-01-08
Definitely install phpMyAdmin, that will get you a usable interface to use with mysql.  You should be able to do everything through that using [http://localhost/phpmyadmin](http://localhost/phpmyadmin) otherwise you will have to use invoke mysql on the command line using

```

mysql

```

---

### Post by tatacalu on 2006-01-08
Done! It works!

Yeey!

---

### Post by tatacalu on 2006-01-09
PHPMyAdmin - Installed OK... Apache2 installed OK.
The question is: in Linux is there the GUI that Apache has under Windows?
Or I shall control apache through the console ? :KS

---

