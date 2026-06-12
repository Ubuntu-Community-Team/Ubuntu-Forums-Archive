---
title: "undo last apt operation?"
date: 2006-07-07
forum: Desktop Environments
---

### Post by calx on 2006-07-07
Hi, is there a way to make **apt** roll back it's last operation?

Obviously there is **remove**, but how about automatically restoring packages removed as the result of an installation?

```
calx@rasta:~$ sudo apt-get install acidlab
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  acidlab-pgsql libapache2-mod-php4 libgd2-xpm libphp-adodb libphp-phplot libt1-5 libzzip-0-12 php4
  php4-common php4-gd php4-pgsql wwwconfig-common
Suggested packages:
  snort-mysql snort-pgsql php-pear libgd-tools postgresql-client apache apache-ssl
Recommended packages:
  php5-pgsql php5-sybase php4-sybase php5-odbc php4-odbc
The following packages will be REMOVED:
  libapache2-mod-php5 libgd2-noxpm php5 php5-mysql php5-mysqli phpmyadmin
The following NEW packages will be installed:
  acidlab acidlab-pgsql libapache2-mod-php4 libgd2-xpm libphp-adodb libphp-phplot libt1-5 libzzip-0-12
  php4 php4-common php4-gd php4-pgsql wwwconfig-common
0 upgraded, 13 newly installed, 6 to remove and 0 not upgraded.
Need to get 3474kB of archives.
After unpacking 11.0MB disk space will be freed.
Do you want to continue [Y/n]? y
```

Oops ](*,)

---

