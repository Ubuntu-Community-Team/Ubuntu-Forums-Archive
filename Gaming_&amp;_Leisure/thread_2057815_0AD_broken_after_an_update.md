---
title: "0AD broken after an update"
date: 2012-09-14
forum: Gaming &amp; Leisure
---

### Post by lz1dsb on 2012-09-14
Few days ago I did the usual update from the update manager. Since than the 0AD game is broken. I can't delete it, and I can't install it. I've got an error saying there's a broken package. The Ubuntu Software Center app offers to repair the broken package, but it also fails to do that. How can I fix it? It's clear that I have a dependency issue...

The following packages have unmet dependencies:

0ad: Depends: 0ad-data (<= 0.0.11-0ubuntu1~11.10~wfg1) but 0.0.0+r11863-1~11.10~wfg1 is installed
     Depends: libboost-filesystem1.46.1 (>= 1.46.1-1) but 1.46.1-5ubuntu2 is installed
     Depends: libboost-signals1.46.1 (>= 1.46.1-1) but 1.46.1-5ubuntu2 is installed
     Depends: libc6 (>= 2.11) but 2.13-20ubuntu5.1 is installed
     Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.21.6-3ubuntu3.2 is installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is installed
     Depends: libjpeg62 (>= 6b1) but 6b1-1ubuntu2 is installed
     Depends: libmozjs185-1.0 (>= 1.8.5~hg20110306r6) but 1.8.5-1.0.0-0ubuntu5 is installed
     Depends: libpng12-0 (>= 1.2.13-4) but 1.2.46-3ubuntu1.3 is installed
     Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.14-6.1ubuntu4 is installed
     Depends: libstdc++6 (>= 4.6) but 4.6.1-9ubuntu3 is installed
     Depends: libvorbisfile3 (>= 1.1.2) but 1.3.2-1ubuntu2.1 is installed
     Depends: libwxbase2.8-0 (>= 2.8.11.0) but 2.8.11.0-0ubuntu10 is installed
     Depends: libwxgtk2.8-0 (>= 2.8.11.0) but 2.8.11.0-0ubuntu10 is installed
     Depends: libxcursor1 (> 1.1.2) but 1:1.1.12-1 is installed
     Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-4ubuntu0.3 is installed
     Depends: zlib1g (>= 1:1.2.0) but 1:1.2.3.4.dfsg-3ubuntu3 is installed
0ad-data-common: Depends: 0ad-data (= 0.0.11-0ubuntu1~11.10~wfg1) but 0.0.0+r11863-1~11.10~wfg1 is installed

---

### Post by raja.genupula on 2012-09-14
open your terminal 

```
sudo apt-get install -f
```

then try again

---

### Post by lz1dsb on 2012-09-23
Hi Raja, 
Thank you for your suggestion. I've tried it. But it still can not resolve the broken dependencies:

:~$ sudo apt-get install -f
[sudo] password for username: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java libntfs10 libkeybinder0 python-keybinder
  libnspr4-0d:i386 libaccess-bridge-java-jni libnss3-1d:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  0ad-data
The following packages will be upgraded:
  0ad-data
1 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
2 not fully installed or removed.
Need to get 0 B/351 MB of archives.
After this operation, 155 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 516324 files and directories currently installed.)
Preparing to replace 0ad-data 0.0.0+r11863-1~11.10~wfg1 (using .../0ad-data_0.0.11-0ubuntu1~11.10~wfg1_all.deb) ...
Unpacking replacement 0ad-data ...
dpkg: error processing /var/cache/apt/archives/0ad-data_0.0.11-0ubuntu1~11.10~wfg1_all.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./usr/share/games/0ad/mods/public/public.zip': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/0ad-data_0.0.11-0ubuntu1~11.10~wfg1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Arthur_D on 2012-09-24
> 
No apport report written because the error message indicates a disk full error
Check if you have enough room on your hard drive. 0 AD. needs a few hundred MB of space.

---

### Post by lz1dsb on 2012-10-03
That's a good one... I really have to check on that. The 0AD package seems to be quite large indeed...

---

### Post by lz1dsb on 2012-10-22
I was able to remove all 0AD packages with Synaptic... Thread closed.

---

