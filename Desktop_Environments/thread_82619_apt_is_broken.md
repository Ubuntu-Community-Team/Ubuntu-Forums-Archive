---
title: "apt is broken"
date: 2005-10-26
forum: Desktop Environments
---

### Post by desleep on 2005-10-26
Well not quite, but I upgraded to openoffice 2 and  removed the  archive directory to make more space on the root partition. Now apt cannot see what is installed and when I tried apt-get install linux-tree I get an error similar to the following, then I try -f and get the following error messages. I think I may have broken it!

root@varuna:/home/paul # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  locales glibc-doc
The following NEW packages will be installed:
  libc6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4821kB of archives.
After unpacking 15.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptor
Preconfiguring packages ...
(Reading database ... 90 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.3.2.ds1-20ubuntu14_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !
dpkg: error processing /var/cache/apt/archives/libc6_2.3.2.ds1-20ubuntu14_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.3.2.ds1-20ubuntu14_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

thanks
P.

---

### Post by Xian on 2005-10-26
Try the following in order:

```
$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/libc6_2.3.2.ds1-20ubuntu14_i386.deb

$ sudo dpkg --configure -a

$ sudo apt-get -f install
```

---

