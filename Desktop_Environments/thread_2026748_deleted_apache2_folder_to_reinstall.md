---
title: "deleted apache2 folder to reinstall"
date: 2012-07-15
forum: Desktop Environments
---

### Post by brainhammer on 2012-07-15
I am new to linux, and I am using Ubuntu 12.04 for some days. I was trying to install few apache modules and messed up thing. Therefore, to install a fresh copy of apache, I uninstalled that running version. I found /etc/apache2 folder is there. I though a fresh install would be better. And therefore I have deleted the /etc/apache2 directory and /etc/init.d/apache2 as well.

But now, I cant install apache again. when I try command  

    ```
sudo apt-get install lamp-server^
```then it shows no error, but when i try:

```
    root@user-Inspiron-N5010:~# service apache2 start
    apache2: unrecognized service
```and in /etc/apache2 directory, only an empty 'mods-available' folder there.

How can I install Apache2 now?

---

### Post by LiftedTurbo on 2012-07-15
Try re-installing it if it already exists.

> sudo apt-get install lamp-server --reinstall

---

### Post by jmfal on 2012-07-15
Welcome to Ubuntu

If you're still having problems try:

```
  sudo apt-get purge lamp-server
                sudo apt-get clean
                sudo apt-get autoclean      
```

Then try and install app

---

### Post by brainhammer on 2012-07-15
Thanks.

I have tried both, but no result .. 
> 
```
  sudo apt-get purge lamp-server
                sudo apt-get clean
                sudo apt-get autoclean      
```

 			 				> 
```
 sudo apt-get install lamp-server --reinstall  			 		
```


```
root@user-Inspiron-N5010:~# sudo apt-get install lamp-server --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package lamp-server
```

and 

```
root@user-Inspiron-N5010:~# sudo apt-get install lamp-server^
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'apache2-utils' for task 'lamp-server'
Note, selecting 'libwrap0' for task 'lamp-server'
Note, selecting 'libnet-daemon-perl' for task 'lamp-server'
Note, selecting 'libclass-isa-perl' for task 'lamp-server'
Note, selecting 'libaprutil1-dbd-sqlite3' for task 'lamp-server'
Note, selecting 'libswitch-perl' for task 'lamp-server'
Note, selecting 'perl' for task 'lamp-server'
Note, selecting 'libcap2' for task 'lamp-server'
Note, selecting 'libhtml-template-perl' for task 'lamp-server'
Note, selecting 'libdbi-perl' for task 'lamp-server'
Note, selecting 'apache2.2-bin' for task 'lamp-server'
Note, selecting 'mysql-client-core-5.5' for task 'lamp-server'
Note, selecting 'libdbd-mysql-perl' for task 'lamp-server'
Note, selecting 'mysql-server-5.5' for task 'lamp-server'
Note, selecting 'libapr1' for task 'lamp-server'
Note, selecting 'mysql-common' for task 'lamp-server'
Note, selecting 'mysql-client-5.5' for task 'lamp-server'
Note, selecting 'libaprutil1-ldap' for task 'lamp-server'
Note, selecting 'apache2-mpm-prefork' for task 'lamp-server'
Note, selecting 'libplrpc-perl' for task 'lamp-server'
Note, selecting 'tcpd' for task 'lamp-server'
Note, selecting 'apache2' for task 'lamp-server'
Note, selecting 'mysql-server-core-5.5' for task 'lamp-server'
Note, selecting 'apache2.2-common' for task 'lamp-server'
Note, selecting 'mysql-server' for task 'lamp-server'
Note, selecting 'ssl-cert' for task 'lamp-server'
Note, selecting 'perl-modules' for task 'lamp-server'
Note, selecting 'libmysqlclient18' for task 'lamp-server'
Note, selecting 'php5-mysql' for task 'lamp-server'
Note, selecting 'php5-cli' for task 'lamp-server'
Note, selecting 'libapache2-mod-php5' for task 'lamp-server'
Note, selecting 'libaprutil1' for task 'lamp-server'
Note, selecting 'php5-common' for task 'lamp-server'
apache2 is already the newest version.
apache2-mpm-prefork is already the newest version.
apache2-utils is already the newest version.
apache2.2-bin is already the newest version.
apache2.2-common is already the newest version.
libapr1 is already the newest version.
libaprutil1 is already the newest version.
libaprutil1-dbd-sqlite3 is already the newest version.
libaprutil1-ldap is already the newest version.
libcap2 is already the newest version.
libclass-isa-perl is already the newest version.
libdbd-mysql-perl is already the newest version.
libdbi-perl is already the newest version.
libhtml-template-perl is already the newest version.
libnet-daemon-perl is already the newest version.
libplrpc-perl is already the newest version.
libswitch-perl is already the newest version.
libwrap0 is already the newest version.
perl is already the newest version.
perl-modules is already the newest version.
tcpd is already the newest version.
libapache2-mod-php5 is already the newest version.
libmysqlclient18 is already the newest version.
mysql-client-5.5 is already the newest version.
mysql-client-core-5.5 is already the newest version.
mysql-common is already the newest version.
mysql-server is already the newest version.
mysql-server-5.5 is already the newest version.
mysql-server-core-5.5 is already the newest version.
php5-cli is already the newest version.
php5-common is already the newest version.
php5-mysql is already the newest version.
ssl-cert is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@user-Inspiron-N5010:~# 

```

---

### Post by brainhammer on 2012-07-15
now seems working >> waiting to check result.
    sudo apt-get install lamp-server^ --reinstall

---

### Post by brainhammer on 2012-07-15
this seems work, but probably missing one file.
```
sudo apt-get install lamp-server^ --reinstall
```mysql is ok. PHP also seems working. But Apache is not.

```
root@user-Inspiron-N5010:~# php --version
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/ming.ini on line 1 in Unknown on line 0
PHP 5.3.10-1ubuntu3.2 with Suhosin-Patch (cli) (built: Jun 13 2012 17:20:55) 
Copyright (c) 1997-2012 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2012 Zend Technologies
root@user-Inspiron-N5010:~# service apache2 restart
apache2: unrecognized service
root@user-Inspiron-N5010:~# service apache2 start
apache2: unrecognized service
root@user-Inspiron-N5010:~# 
```I have checked the /etc/init.d/ and here is no file names apache [i have deleted the first one .. :( ].. may be missing this one... 

any suggestion?

---

### Post by jmfal on 2012-07-15
Try this
```
  sudo apt-get install -f   
```

---

### Post by brainhammer on 2012-07-15
> **jmfal said:**
> Try this
```
  sudo apt-get install -f   
```

not working... :(

---

### Post by jmfal on 2012-07-15
Try this
```
   
sudo apt-get remove --purge apache2 apache2-common sudo apt-get install --reinstall apache2 apache2-common    
```

---

### Post by jmfal on 2012-07-15
That didn't copy/paste right

```
     
sudo apt-get remove --purge apache2 apache2-common    
```    
```
  
sudo apt-get install --reinstall apache2 apache2-common   
```

---

### Post by brainhammer on 2012-07-15
here is the output:::

```
root@user-Inspiron-N5010:~# sudo apt-get install --reinstall apache2 apache2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  apache2.2-common apache2-utils

E: Package 'apache2-common' has no installation candidate
root@user-Inspiron-N5010:~# 
```

---

### Post by jmfal on 2012-07-15
```
 sudo apt-get install apache2.2-common
              sudo apt-get install apache2-utils
```

If that doesn't work open synaptic and install from there.

---

### Post by brainhammer on 2012-07-15
not working.. I found both are installed in Ubuntu Software Center, when I remove first one, both removed, and when I install that one - both installed at a time.

but message is same:
```
root@user-Inspiron-N5010:~# service apache2 start
apache2: unrecognized service
root@user-Inspiron-N5010:~# 

```

---

### Post by jmfal on 2012-07-15
Try
 ```
 sudo service apache2 start    
```

---

### Post by brainhammer on 2012-07-15
same...
-----
root@user-Inspiron-N5010:~#  sudo service apache2 start
apache2: unrecognized service
root@user-Inspiron-N5010:~# 
-----

---

### Post by jmfal on 2012-07-16
I don't know what to tell you .
I didn't have any problems setting mine up.
Take a look at this:

[http://askubuntu.com/questions/26228/how-can-i-replace-missing-configuration-files-after-removing-a-package](http://askubuntu.com/questions/26228/how-can-i-replace-missing-configuration-files-after-removing-a-package)

---

### Post by brainhammer on 2012-07-16
Thanks for your effort.
I have re-installed Ubuntu. Setting up everything from the beginning.

---

