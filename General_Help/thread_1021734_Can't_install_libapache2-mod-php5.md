---
title: "Can't install libapache2-mod-php5"
date: 2008-12-25
forum: General Help
---

### Post by smcfarland on 2008-12-25
Seems like it is trying to install ucf_2.0017ubuntu1_all.deb, which is no longer available on any of the mirrors. Any ideas of what I can do? I am running Ubuntu 7.04

> apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  ucf
Suggested packages:
  php-pear
Recommended packages:
  debconf-utils
The following NEW packages will be installed:
  libapache2-mod-php5 ucf
0 upgraded, 2 newly installed, 0 to remove and 40 not upgraded.
Need to get 57.0kB/2712kB of archives.
After unpacking 6623kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  ucf
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main ucf 2.0017ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ucf/ucf_2.0017ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ucf/ucf_2.0017ubuntu1_all.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Thanks,
Scott

---

### Post by Tipo on 2008-12-25
Have you run the apt-get update as the error suggests?

Also, are you running apt-get with sudo?

---

### Post by utnubuuser on 2008-12-26
Hi, Merry Christmas --

Aren't all the Feisty Fawn repos closed now?
Might be possible to get the package through the Gutsy Gibbon repo.

I liked Feisty too, but 8.10 is running perfectly on equipment the ran very well on Feisty.

---

### Post by p_quarles on 2008-12-26
> **utnubuuser said:**
> Aren't all the Feisty Fawn repos closed now?
Yes, they are. Ubuntu 7.04 is no longer supported. The OP should upgrade to a supported version of Ubuntu. 

Thread closed.

---

