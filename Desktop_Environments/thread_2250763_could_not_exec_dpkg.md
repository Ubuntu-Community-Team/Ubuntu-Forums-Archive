---
title: "could not exec dpkg"
date: 2014-10-30
forum: Desktop Environments
---

### Post by caron.mark on 2014-10-30
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
cadmin@cadmin:~$ sudo dpkg -configure 
sudo: dpkg: command not found
cadmin@cadmin:~$ sudo dpkg-reconfigure -a
Can't exec "dpkg": No such file or directory at /usr/sbin/dpkg-reconfigure line 82.
Use of uninitialized value $_ in pattern match (m//) at /usr/sbin/dpkg-reconfigure line 83.
Use of uninitialized value $_ in pattern match (m//) at /usr/sbin/dpkg-reconfigure line 84.
Use of uninitialized value $_ in pattern match (m//) at /usr/sbin/dpkg-reconfigure line 85.
Use of uninitialized value $_ in pattern match (m//) at /usr/sbin/dpkg-reconfigure line 86.
/usr/sbin/dpkg-reconfigure: accountsservice is not installed

cadmin@cadmin:~$ sudo apt-get install dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1066 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
cadmin@cadmin:~$

---

