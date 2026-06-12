---
title: "Updates not working"
date: 2005-05-07
forum: Desktop Environments
---

### Post by sprucio on 2005-05-07
I just installed Kubuntu this week and already, it's having problems when I run "apt-get dist-upgrade." From what I can make out, one of the packages is conf. Here's the exact thing when I run it.

```
[root@pine bpark]# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 

Preconfiguring packages ...
(Reading database ... 60460 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3
.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1
_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package kn
etworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 
Any ideas?

---

### Post by dodger on 2005-05-07
it's a bug

[http://www.ubuntuforums.org/showthread.php?t=28678](http://www.ubuntuforums.org/showthread.php?t=28678)

---

