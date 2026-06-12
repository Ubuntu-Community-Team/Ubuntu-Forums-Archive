---
title: "php5-pear"
date: 2006-10-04
forum: Desktop Environments
---

### Post by cope on 2006-10-04
Hey Guys, 

I'm having trouble installing php5-pear, 

```

mark> sudo apt-get install php5-pear
Reading package lists... Done
Building dependency tree... Done
Package php5-pear is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php5-pear has no installation candidate
mark>

```

these are my install php5 packages
```
ls /var/cache/apt/archives/ | grep "php5"
```

```

libapache2-mod-php5_5.1.2-1ubuntu3.2_i386.deb
php5_5.1.2-1ubuntu3.2_all.deb
php5-cli_5.1.2-1ubuntu3.2_i386.deb
php5-common_5.1.2-1ubuntu3.2_i386.deb
php5-mysql_5.1.2-1ubuntu3.2_i386.deb
php5-mysqli_5.1.2-1ubuntu3.2_i386.deb

```

can anyone help?

---

### Post by odinfromvalhalla on 2006-10-04
i think php-pear is the package you need to install for php5.

let me know if that works.

---

### Post by lkagan on 2006-10-04
I second that:  Here's my pear package listing:
```
larry@spanky:~$ dpkg -l | grep pear
ii  php-pear                               5.1.2-1ubuntu3.2 
```

Larry Kagan

---

