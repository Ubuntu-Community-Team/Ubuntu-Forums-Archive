---
title: "MD5Sum mismatch"
date: 2005-06-11
forum: Desktop Environments
---

### Post by adamb10 on 2005-06-11
Hi all,
   When I try to install gstreamer0.8-plugins I get this output:

> 
root@ubuntu:/home/adam # apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-sid gstreamer0.8-swfdec jackd
  liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0 libmikmod2 libmpeg2-4
  libsidplay1-c102 libsndfile1 libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0
  libmikmod2 libmpeg2-4 libsidplay1-c102 libsndfile1 libswfdec0.3
0 upgraded, 22 newly installed, 0 to remove and 2 not upgraded.
Need to get 1174kB of archives.
After unpacking 3486kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main liba52-0.7.4 0.7.4-1 [25.1kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gstreamer0.8-a52dec 0.8.8-1ubuntu4 [32.3kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-aa 0.8.8-1ubuntu4 [31.7kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-artsd 0.8.8-1ubuntu4 [29.3kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-caca 0.8.8-1ubuntu4 [43.5kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-festival 0.8.8-1ubuntu4 [29.2kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libsndfile1 1.0.10-2 [164kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main jackd 0.99.0-2ubuntu1 [84.8kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libjack0.80.0-0 0.99.0-2ubuntu1 [66.2kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-jack 0.8.8-1ubuntu4 [31.8kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libid3tag0 0.15.1b-3 [34.2kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libmad0 0.15.1b-1 [73.1kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gstreamer0.8-mad 0.8.8-1ubuntu4 [50.4kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libmikmod2 3.1.11-a-6ubuntu2 [124kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-mikmod 0.8.8-1ubuntu4 [32.1kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libmpeg2-4 0.4.0b-2ubuntu1 [60.6kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gstreamer0.8-mpeg2dec 0.8.8-1ubuntu4 [40.0kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libsidplay1-c102 1.36.59-2 [73.2kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-sid 0.8.8-1ubuntu4 [32.2kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libswfdec0.3 0.3.2-2 [61.2kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gstreamer0.8-swfdec 0.8.8-1ubuntu4 [31.2kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gstreamer0.8-plugins 0.8.8-1ubuntu4 [23.9kB]
Fetched 1174kB in 8s (131kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.10-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.10-2_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


This happens when I try to install gftp also.

---

### Post by Xian on 2005-06-11
Check [THIS](http://www.ubuntuforums.org/showthread.php?p=208396#post208396) thread for more info.

---

### Post by adamb10 on 2005-06-11
[QUOTE=Xian]Check [THIS](http://www.ubuntuforums.org/showthread.php?p=208396#post208396) thread for more info.[/QUOTE]
 thanx

---

