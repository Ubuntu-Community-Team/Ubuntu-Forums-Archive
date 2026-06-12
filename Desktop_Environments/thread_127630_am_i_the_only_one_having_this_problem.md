---
title: "am i the only one having this problem?"
date: 2006-02-09
forum: Desktop Environments
---

### Post by rudeboyskunk on 2006-02-09
root@ashbysucks:/home/rudeboyskunk# apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-lame
root@ashbysucks:/home/rudeboyskunk#

---

### Post by Ramses de Norre on 2006-02-09
What are your repo's like? Have you uncommented the multiverse & universe repo's? (you find them at /etc/apt/sources.list)
run sudo apt-get update after changing them.

---

### Post by jonathanm on 2006-02-09
sudo?? shouldnt come up with that error though maybe something up with your network

---

### Post by aysiu on 2006-02-09
Something's wrong with your sources.list.
See the first link of my signature. Then, try again.

---

### Post by rudeboyskunk on 2006-02-09
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free



I added the last two in a few hours ago, but every time I do an apt-get update, it just says "Ign" by them.  Strangely enough, I can install sun-j2re1.5 from that source...

---

### Post by rudeboyskunk on 2006-02-09
[QUOTE=aysiu]Something's wrong with your sources.list.
See the first link of my signature. Then, try again.[/QUOTE]


Thank you so much!  This worked perfectly.  You're my hero now.

---

