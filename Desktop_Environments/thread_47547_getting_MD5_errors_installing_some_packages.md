---
title: "getting MD5 errors installing some packages"
date: 2005-07-09
forum: Desktop Environments
---

### Post by johnio on 2005-07-09
Is there anyway I can just try to ignore these errors? All I care about installing is the libqt3-mt-dev package.

sudo apt-get install libqt3-mt-dev Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libjpeg62-dev libmng-dev libpng12-dev
Suggested packages:
  libqt3-i18n qt3-doc
Recommended packages:
  libqt3-compat-headers
The following NEW packages will be installed:
  libjpeg62-dev libmng-dev libpng12-dev libqt3-mt-dev
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 421kB/715kB of archives.
After unpacking 2023kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libjpeg62-dev 6b-9 [181kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libpng12-dev 1.2.8rel-1 [241kB]
Fetched 421kB in 1s (296kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg62-dev_6b-9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg62-dev_6b-9_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by NeoChaosX on 2005-07-09
Same problem here. When I try to install mplayer, I get this message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgii/libgii0_0.8.5-2_i386.deb)  MD5Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libggi/libggi2_2.0.5-1ubuntu1_i386.deb)  MD5Sum mismatch

What's going on? Did something go wrong with some of the packages on the main Ubuntu repos?

---

### Post by johnio on 2005-07-09
found a bunch of bugs for it

[https://bugzilla.ubuntu.com/show_bug.cgi?id=11793](https://bugzilla.ubuntu.com/show_bug.cgi?id=11793)

seems the fix is try a non us mirror

---

### Post by ImaMadGoat on 2005-07-09
I got those problems too. I got around them by copying the url that had the mismatch and pasting it in google. Google will tell you it couldn't find any results for your entry but it will make the url a link that you can 'save link as'. Save it to your home folder and then go to your terminal.

type

sudo dpkg -i (the filename of the deb package you saved)

that should take care of it.

btw, if you can spare 40 bucks or find a way to get a copy of crossover office, it will let you play itunes in linux. That's what I use for all my audio. I love it

Chad

---

### Post by MikeyXX on 2005-07-09
[QUOTE=ImaMadGoat]I got those problems too. I got around them by copying the url that had the mismatch and pasting it in google. Google will tell you it couldn't find any results for your entry but it will make the url a link that you can 'save link as'. Save it to your home folder and then go to your terminal.

type

sudo dpkg -i (the filename of the deb package you saved)

that should take care of it.

btw, if you can spare 40 bucks or find a way to get a copy of crossover office, it will let you play itunes in linux. That's what I use for all my audio. I love it

Chad[/QUOTE]
 Hey Chad, 

I tried what you suggested when I got an error and I ended up with this:

root@ltubuntu:/home/michael # sudo dpkg -i libcairo1_0.3.0-1_i386.deb
dpkg-deb: `libcairo1_0.3.0-1_i386.deb' is not a debian format archive
dpkg: error processing libcairo1_0.3.0-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 libcairo1_0.3.0-1_i386.deb

I had set apt-get to upgrade the system. It picked it's files and errored only on this.

---

### Post by ibanez88 on 2005-07-09
Remove "us" from your sources in /etc/apt/sources.list

I had the same problem with libcairo1.  This should take care of it.

---

