---
title: "apt problems"
date: 2005-07-09
forum: Desktop Environments
---

### Post by terrien on 2005-07-09
WEll, I just installed Kubuntu (off of the cd), and when I try to install a few things (Synaptic in this case), I get this error:

```
frosty@rivaridge:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libatk1.0-0 libglade2-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libpango1.0-0 libpango1.0-common libvte-common libvte4
Suggested packages:
  ttf-thryomanes
Recommended packages:
  libatk1.0-data gksu deborphan libgnome2-perl
The following NEW packages will be installed:
  libatk1.0-0 libglade2-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libpango1.0-0 libpango1.0-common libvte-common libvte4 synaptic
0 upgraded, 10 newly installed, 0 to remove and 3 not upgraded.
Need to get 1875kB/4833kB of archives.
After unpacking 22.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  synaptic
Install these packages without verification [y/N]? y
Get:1 http://ubuntu-backports.mirrormax.net hoary-backports/main synaptic 0.56+revertedto+officialhoary+0.55+cvs20050406-1~5.04ubp1 [1611kB]
Get:2 http://us.archive.ubuntu.com hoary/main libpango1.0-0 1.8.1-0ubuntu2 [264kB]
Fetched 1875kB in 9s (191kB/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.8.1-0ubuntu2_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
``` 

I've tried the apt-get update, but --fix-missing doesn't seem to do anything... Anyone know how to fix this?

---

### Post by adwait on 2005-07-09
try changing the respositories to archive.ubuntu.com instead of us.archive.ubuntu.com . You the do that using

sudo gedit /etc/apt/sources.list

---

### Post by terrien on 2005-07-09
Thanks so much! It's working perfectly now!

---

