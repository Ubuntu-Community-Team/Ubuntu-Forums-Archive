---
title: "Ouch!  Got SIGSEGV, dying.. Segmentation fault"
date: 2009-05-27
forum: General Help
---

### Post by Vik Vasilev on 2009-05-27
So, I`ve been using Ubuntu for 3-4 months, in the last one I fully switched to it cause i think I learned to work with it well enough. 

Something happened with my package managers today (No im really not such a noob) but i dont what caused it. Add/Remove programs and Synaptic crash before the windows even loads, and aptitude give me this error code:
[B]
root@vik-desktop:~# aptitude
Ouch!  Got SIGSEGV, dying..
Segmentation fault


[/B]I`m using Ubuntu 9.04
Any ideas how to fix this? I dont want to reinstall again

---

### Post by Vik Vasilev on 2009-05-27
bump

---

### Post by Soul-Sing on 2009-05-27
Could you please put your sources.lst here?
And are there problems updating&upgrading?

---

### Post by Vik Vasilev on 2009-05-27
My update manager doesnt start like the package managers. Shows up for less than a second and dissapears 

Sources.list from etc/apt
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://bg.archive.ubuntu.com/ubuntu/ jaunty main restricted universe
deb-src http://bg.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://bg.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe
deb-src http://bg.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://bg.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://bg.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://bg.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://bg.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://bg.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://bg.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://bg.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://bg.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://bg.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://bg.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

### Post by Soul-Sing on 2009-05-27
Strange.....

Would you please uninstall aptitude and reinstall it again.
I hope very much that this solves your problem.
( Use synaptic)

---

### Post by trinoquad on 2009-06-03
I had the same problem and since i had no choice to reinstall,first i tried changing the server from where i get the updates.
... here is what i did.
Under System...> Administration...>Software Resources...> Tab..Ubuntu Software... Download From..(Choose a different one.)... I had one from umn.edu server, so i changed to the United States Server and Clicked Ok... Ok and the update got downloaded and installed.

... THe problems stopped showing...i hope the bug gets fixed.

Gook Luck|*

---

### Post by techningeer on 2010-08-27
It's a problem with the package DB. It has been a problem since 8.10. So, just run "apt-get update" as root. It should work after that.

---

### Post by jmullee on 2011-05-26
```


root@johnm-VirtualBox:~# aptitude

### aptitude reported some downloaded archive was a corrupted bzip

### /var/log/aptitude:
	Aptitude 0.6.3: log report
	Thu, May 26 2011 08:57:01 +0100

	IMPORTANT: this log only lists intended actions; actions which fail due to
	dpkg problems may not be completed.

	Will install 5 packages, and remove 0 packages.
	8,192B of disk space will be used
	===============================================================================
	[UPGRADE] language-selector 0.6.8+langfixes~maverick1 -> 0.6.8+langfixes~maverick2
	[UPGRADE] language-selector-common 0.6.8+langfixes~maverick1 -> 0.6.8+langfixes~maverick2
	[UPGRADE] libapr1 1.4.2-3ubuntu1 -> 1.4.2-3ubuntu1.1
	[UPGRADE] libapr1-dev 1.4.2-3ubuntu1 -> 1.4.2-3ubuntu1.1
	[UPGRADE] rdesktop 1.6.0-3ubuntu2 -> 1.6.0-3ubuntu2.1
	===============================================================================

	Log complete.
###

(Reading database ... 222652 files and directories currently installed.)
Preparing to replace language-selector 0.6.8+langfixes~maverick1 (using .../language-selector_0.6.8+langfixes~maverick2_all.deb) ...
Unpacking replacement language-selector ...
Preparing to replace language-selector-common 0.6.8+langfixes~maverick1 (using .../language-selector-common_0.6.8+langfixes~maverick2_all.deb) ...
Unpacking replacement language-selector-common ...
Preparing to replace libapr1-dev 1.4.2-3ubuntu1 (using .../libapr1-dev_1.4.2-3ubuntu1.1_amd64.deb) ...
Unpacking replacement libapr1-dev ...
Preparing to replace libapr1 1.4.2-3ubuntu1 (using .../libapr1_1.4.2-3ubuntu1.1_amd64.deb) ...
Unpacking replacement libapr1 ...
Preparing to replace rdesktop 1.6.0-3ubuntu2 (using .../rdesktop_1.6.0-3ubuntu2.1_amd64.deb) ...
Unpacking replacement rdesktop ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up language-selector-common (0.6.8+langfixes~maverick2) ...
Setting up libapr1 (1.4.2-3ubuntu1.1) ...
Setting up libapr1-dev (1.4.2-3ubuntu1.1) ...
Setting up rdesktop (1.6.0-3ubuntu2.1) ...
Processing triggers for python-central ...
Setting up language-selector (0.6.8+langfixes~maverick2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-central ...
Press return to continue.

Ouch!  Got SIGSEGV, dying..
Segmentation fault
root@johnm-VirtualBox:~# apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 0%

### aptitude crashed! oops!


### lets try .. - backup/remove pkgcache.bin ..

root@johnm-VirtualBox:~# mv /var/cache/apt/pkgcache.bin /var/cache/apt/pkgcache.bin_

### lets try .. - and removing foreign sources

root@johnm-VirtualBox:~# vim /etc/apt/sources.list.d/rabbitvcs-ppa-maverick.list
root@johnm-VirtualBox:~# cat /etc/apt/sources.list.d/rabbitvcs-ppa-maverick.list
	#deb http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu maverick main
	#deb-src http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu maverick main

root@johnm-VirtualBox:~# apt-get update && apt-get upgrade

### operates without error, OK.

root@johnm-VirtualBox:~# l /var/cache/apt/pkgcache.bin /var/cache/apt/pkgcache.bin_
 -rw-r--r-- 1 root 18855614 2011-05-26 08:57 /var/cache/apt/pkgcache.bin_
 -rw-r--r-- 1 root 18855206 2011-05-26 09:05 /var/cache/apt/pkgcache.bin

### reenable rabbitvcs, will it work ?

root@johnm-VirtualBox:~# vim /etc/apt/sources.list.d/rabbitvcs-ppa-maverick.list
root@johnm-VirtualBox:~# apt-get update && apt-get upgrade
root@johnm-VirtualBox:~# strings /var/cache/apt/pkgcache.bin > /tmp/c
root@johnm-VirtualBox:~# l /tmp/a /tmp/c
3376 -rw-r--r-- 1 root 3455009 2011-05-26 09:06 /tmp/a
3376 -rw-r--r-- 1 root 3455009 2011-05-26 09:18 /tmp/c
root@johnm-VirtualBox:~# md5sum /tmp/a /tmp/c
a60754ff9fa3eed69cfd0dab08261c7d  /tmp/a
a60754ff9fa3eed69cfd0dab08261c7d  /tmp/c

### works OK

### what diff in the pkgcache file ?

root@johnm-VirtualBox:~# cat /var/cache/apt/pkgcache.bin_ | hexdump -C > /tmp/pkgcache.broken
root@johnm-VirtualBox:~# cat /var/cache/apt/pkgcache.bin | hexdump -C > /tmp/pkgcache.fixed
root@johnm-VirtualBox:~# wc -l /tmp/pkgcache.broken /tmp/pkgcache.fixed
  1172855 /tmp/pkgcache.broken
  1172855 /tmp/pkgcache.fixed
  2345710 total
root@johnm-VirtualBox:~# diff -U 10 /tmp/pkgcache.broken /tmp/pkgcache.fixed
--- /tmp/pkgcache.broken	2011-05-26 09:23:27.185149002 +0100
+++ /tmp/pkgcache.fixed	2011-05-26 09:23:42.415149001 +0100
@@ -794720,22 +794720,22 @@
 00c263a0  00 00 00 00 00 00 00 00  a5 0d c3 00 c8 83 01 00  |................|
 00c263b0  ea b0 02 00 00 00 00 00  56 b8 43 00 f0 7b 09 00  |........V.C..{..|
 00c263c0  9e 5a 03 00 f0 f4 06 00  00 00 00 00 00 00 00 00  |.Z..............|
 00c263d0  07 82 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
 00c263e0  05 0e c3 00 c8 83 01 00  ec b0 02 00 00 00 00 00  |................|
 00c263f0  56 b8 43 00 f1 7b 09 00  1b 02 03 00 ee f4 06 00  |V.C..{..........|
 00c26400  00 00 00 00 00 00 00 00  08 82 00 00 00 00 00 00  |................|
 00c26410  00 00 00 00 00 00 00 00  0e 0e c3 00 c8 83 01 00  |................|
 00c26420  00 00 00 00 00 00 00 00  00 00 00 00 f2 7b 09 00  |.............{..|
 00c26430  40 5d 03 00 f2 f4 06 00  00 00 00 00 00 00 00 00  |@]..............|
-00c26440  34 40 50 00 00 00 00 a0  00 00 00 00 00 00 00 00  |4@P.............|
-00c26450  00 00 00 00 c8 83 01 00  00 00 50 00 01 00 00 00  |..........P.....|
+00c26440  09 82 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
+00c26450  74 0e c3 00 c8 83 01 00  ed b0 02 00 00 00 00 00  |t...............|
 00c26460  50 5c 43 00 f3 7b 09 00  d2 6a 03 00 cb 04 08 00  |P\C..{...j......|
 00c26470  00 00 00 00 00 00 00 00  0a 82 00 00 00 00 00 00  |................|
 00c26480  00 00 00 00 00 00 00 00  ab 0e c3 00 c8 83 01 00  |................|
 00c26490  ee b0 02 00 00 00 00 00  1d ac 4c 00 f4 7b 09 00  |..........L..{..|
 00c264a0  e7 1e 03 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
 00c264b0  0b 82 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
 00c264c0  0e 0f c3 00 c8 83 01 00  ef b0 02 00 00 00 00 00  |................|
 00c264d0  fe d8 47 00 f5 7b 09 00  73 78 03 00 00 00 00 00  |..G..{..sx......|
 00c264e0  00 00 00 00 00 00 00 00  0c 82 00 00 00 00 00 00  |................|
 00c264f0  00 00 00 00 00 00 00 00  a1 0f c3 00 c8 83 01 00  |................|



```

---

### Post by techningeer on 2011-05-27
Hi everybody,
     Try these commands:
```
sudo rm -f /var/cache/apt/*.bin
```
```
sudo aptitude update
```

I think that the package cache got corrupted. Those commands above will clear the package cache and refresh the package lists. Remember that you MUST do both.

Let me know how it goes!

--techningeer

---

### Post by mytinytown on 2011-10-11
> **techningeer said:**
> Hi everybody,
     Try these commands:
```
sudo rm -f /var/cache/apt/*.bin
```
```
sudo aptitude update
```

I think that the package cache got corrupted. Those commands above will clear the package cache and refresh the package lists. Remember that you MUST do both.

Let me know how it goes!

--techningeer

I was having apt-get issues too.

Your code worked to clear my issue!!!

Thank you!!!!!!

---

