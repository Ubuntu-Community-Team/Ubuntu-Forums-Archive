---
title: "Installing mame - Pkg Missing All Reps are added"
date: 2005-11-18
forum: Gaming &amp; Leisure
---

### Post by pkraus on 2005-11-18
Is the xmame pkg no longer available.  I am trying to install mame (i have never used this before) and following a couple threads in these forums they all call for you to do an apt-get for the pkg xmame-x. I cann't find the pkg. A search for mame comes up with nothing.

TIA,
Paul

pkraus@pkraus:~$ sudo apt-get install xmame-x
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmame-x

pkraus@pkraus:~$ sudo apt-cache search mame
pcrd - PCR-1000 Control Daemon / Command Line Interface
xwnc - Mix of Xvnc and XDarwin with improved protocol

pkraus@pkraus:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main r estricted

Sources File.
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
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted u niverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://www.mwolson.org/debian/](http://www.mwolson.org/debian/) ./

---

