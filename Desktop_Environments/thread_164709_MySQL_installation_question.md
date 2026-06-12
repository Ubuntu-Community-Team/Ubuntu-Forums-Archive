---
title: "MySQL installation question"
date: 2006-04-23
forum: Desktop Environments
---

### Post by izzyonstage on 2006-04-23
Hi,
I am trying to find out where i can get the MySQL package that will run on ubuntu and how to install it.

Can anyone help me?

---

### Post by bihe on 2006-04-23
~# sudo apt-get install mysql-server

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0 mysql-server-5.0
Suggested packages:
  dbishell libcompress-zlib-perl
Recommended packages:
  mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0 mysql-server mysql-server-5.0
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.0MB of archives.
After unpacking 62.6MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

