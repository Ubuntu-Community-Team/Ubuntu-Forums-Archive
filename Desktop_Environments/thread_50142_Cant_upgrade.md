---
title: "Cant upgrade"
date: 2005-07-19
forum: Desktop Environments
---

### Post by tflovik on 2005-07-19
I have a problem using backports and KDE 3.4.1 repos.
Here is my sources.list:
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.4.1/kubuntu](ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.4.1/kubuntu) hoary-updates main

Here is what i get running apt-get update :
tflovik@ubuntu:~$ sudo apt-get update
Hent:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hent:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources
Fant [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources
Hent:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Fant [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Fant [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Fant [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Fant [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Fant [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Fant [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Fant [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Fant [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Fant [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hent:4 [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) hoary-updates Release.gpg
Fant [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Fant [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Fant [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Fant [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Fant [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Fant [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Ign [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) hoary-updates Release.gpg
Hent:5 [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) hoary-updates Release
Ign [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) hoary-updates Release
Hent:6 [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) hoary-updates/main Packages
Ign [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) hoary-updates/main Packages
Fant [ftp://bolugftp.uni-bonn.de](ftp://bolugftp.uni-bonn.de) hoary-updates/main Packages
Skaffet 3B på 9s (0B/s)
Reading package lists... Done

Trying to run apt-get upgrade provides no packages.
Security updates work.

Can anybody help?

---

### Post by tflovik on 2005-07-19
I have solved it.
The solution was to remove all contents from the file:
/etc/apt/preferences.

---

