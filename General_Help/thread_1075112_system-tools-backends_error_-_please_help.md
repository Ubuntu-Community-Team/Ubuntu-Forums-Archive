---
title: "system-tools-backends error - please help"
date: 2009-02-19
forum: General Help
---

### Post by ddigler on 2009-02-19
Every time I try to install a package with synaptic I get this error:

E: system-tools-backends: subprocess post-installation script returned error exit status 1. 

I tried copying the details log but was not able to.

Any help is greatly appreciated! :)

---

### Post by Yellow Pasque on 2009-02-19
Try to get more detailed output by running in a terminal:
```
sudo dpkg --configure -a
```
or maybe
```
sudo apt-get install <packagename>
```

---

### Post by ddigler on 2009-02-19
zac@Home-Office-PC:~$ sudo dpkg --configure -a
[sudo] password for zac: 
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends

zac@Home-Office-PC:~$ sudo apt-get install system-tools-backends
Reading package lists... Done
Building dependency tree       
Reading state information... Done
system-tools-backends is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends

---

### Post by Yellow Pasque on 2009-02-19
```
sudo invoke-rc.d system-tools-backends stop
sudo dpkg --configure -a
```
[https://lists.ubuntu.com/archives/ubuntu-main-sponsors/2008-November/009348.html](https://lists.ubuntu.com/archives/ubuntu-main-sponsors/2008-November/009348.html)

---

### Post by ddigler on 2009-02-20
Problem fixed, thank you!

---

