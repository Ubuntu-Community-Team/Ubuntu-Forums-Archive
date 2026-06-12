---
title: "Error Installing ClamAV"
date: 2006-06-05
forum: Desktop Environments
---

### Post by kozmo on 2006-06-05
I did a LAMP install from the server edition, but when I try to install **clamav** I get errors. Here is the log file output:                                                                 
                                                                     
                                             
manager@msgsapjy3yr11lin:~$ sudo apt-get install clamav
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  ca-certificates clamav-base clamav-freshclam libclamav1 libcurl3 libgmp3c2
  libidn11 ucf
Suggested packages:
  unrar lha clamav-docs
Recommended packages:
  arj unzoo debconf-utils
The following NEW packages will be installed:
  ca-certificates clamav clamav-base clamav-freshclam libclamav1 libcurl3
  libgmp3c2 libidn11 ucf
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 4797kB/5510kB of archives.
After unpacking 7586kB of additional disk space will be used.
Do you want to continue [Y/n]?
Media change: please insert the disc labeled
 'Ubuntu-Server 6.06 _Dapper Drake_ - Release Candidate i386 (20060524.2)'
in the drive '/cdrom/' and press enter

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe libclamav1 0.88.2-1ubuntu1 [263kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe clamav-base 0.88.2-1ubuntu1 [172kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe clamav-freshclam 0.88.2-1ubuntu1 [4297kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe clamav 0.88.2-1ubuntu1 [65.7kB]
Fetched 4797kB in 48s (98.2kB/s)
Preconfiguring packages ...
Selecting previously deselected package ca-certificates.
(Reading database ... 18033 files and directories currently installed.)
Unpacking ca-certificates (from .../ca-certificates_20050804_all.deb) ...
Selecting previously deselected package libidn11.
Unpacking libidn11 (from .../libidn11_0.5.18-1_i386.deb) ...
Selecting previously deselected package libcurl3.
Unpacking libcurl3 (from .../libcurl3_7.15.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package libgmp3c2.
Unpacking libgmp3c2 (from .../libgmp3c2_4.1.4-11ubuntu2_i386.deb) ...
Selecting previously deselected package libclamav1.
Unpacking libclamav1 (from .../libclamav1_0.88.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package ucf.
Unpacking ucf (from .../main/u/ucf/ucf_2.004_all.deb) ...
Moving old data out of the way
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.88.2-1ubuntu1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.88.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.88.2-1ubuntu1_i386.deb) ...
Setting up ca-certificates (20050804) ...
Updating certificates in /etc/ssl/certs....done.

Setting up libidn11 (0.5.18-1) ...

Setting up libcurl3 (7.15.1-1ubuntu2) ...

Setting up libgmp3c2 (4.1.4-11ubuntu2) ...

Setting up libclamav1 (0.88.2-1ubuntu1) ...

Setting up ucf (2.004) ...

Setting up clamav-base (0.88.2-1ubuntu1) ...
Adding system user `clamav'...
Adding new group `clamav' (111).
Adding new user `clamav' (111) with group `clamav'.
Not creating home directory `/var/lib/clamav'.
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.88.2-1ubuntu1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
manager@msgsapjy3yr11lin:~$

Any ideas on what is going on?
Thanks!

---

### Post by linuchsan on 2006-06-05
you have to install clamav-freshclam.
apt-get install clamav clamav-freshclam

---

