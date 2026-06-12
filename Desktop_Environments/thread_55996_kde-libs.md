---
title: "kde-libs"
date: 2005-08-10
forum: Desktop Environments
---

### Post by kheno on 2005-08-10
Hey guys, i installed kubuntu ! and i'm having some problems in it:

when i tried to install nmap it returned me a error that my kdelibs version is too old, when i tried apt-get upgrade:

```
kheno@exodia:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdelibs: Depends: kdelibs-data (>= 4:3.4.0-0ubuntu3.3) but 4:3.4.0-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.
```
and i thought: "okkk lets try this now" then, i type:
sudo apt-get -f install and it returned me:
```
kheno@exodia:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
6 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 87661 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.3_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.3_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

thanks and see ya

---

### Post by David R on 2005-08-11
I think you should first try to update your KDE 3.4.0 to the 3.4.2 version.

To do that, you will need to add the following line to your repositories list in Synaptic :
deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

---

