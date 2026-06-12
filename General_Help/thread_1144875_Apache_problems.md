---
title: "Apache problems"
date: 2009-05-01
forum: General Help
---

### Post by Primefalcon on 2009-05-01
I have installed the latest jaunty jackalope and I seem to be having problems with apache

specificaly the 

 apache2-mpm-prefork
 libapache2-mod-php5


packages I've tried uninstalling these and reinstalling am having a hell load of trouble, is there some bug here or something? I just can't get apache working here

an aptitude remove got me this

```

brad@blackbeard:~$ sudo aptitude remove apache2-mpm-prefork
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  apache2-mpm-prefork{u} libapache2-mod-php5{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 6087kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 103247 files and directories currently installed.)
Removing libapache2-mod-php5 ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing libapache2-mod-php5 (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Removing apache2-mpm-prefork ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing apache2-mpm-prefork (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 libapache2-mod-php5
 apache2-mpm-prefork
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

brad@blackbeard:~$ 


```

---

### Post by Primefalcon on 2009-05-01
I try to reinstall these packages and I get

E: apache2-mpm-prefork: subprocess post-installation script returned error exit status 2
E: libapache2-mod-php5: dependency problems - leaving unconfigured

I can't uninstall/reinsstall or anything with this............

---

### Post by Primefalcon on 2009-05-01
ok just tried even using a --force-yes and just comes back the same error....

---

### Post by Primefalcon on 2009-05-01
I just tried an aptitude remove and amended the output to the first post

---

### Post by Primefalcon on 2009-05-01
Ok I seem to have gotten the file removed by using

```
sudo rm /var/lib/dpkg/info/"offending packages"*
```

gonna try a reinstall of apache now, let's see what happens, wish me luck

---

### Post by Primefalcon on 2009-05-01
ok seems to ahve worked but apache won't start.... on trying to start it I get this

```

brad@blackbeard:~$ sudo /etc/init.d/apache2 start
.: 44: Can't open /etc/apache2/envvars
brad@blackbeard:~$ 

```

---

### Post by comandrei on 2009-05-01
try reinstalling the apache packages and then removing it, and use apt-get autoremove to remove unused depedencies

---

### Post by Primefalcon on 2009-05-01
I just did something similar now I purged and reinstalled, now it's working, wonder what the hell happened initially with apache though with the mpm worker.......

---

