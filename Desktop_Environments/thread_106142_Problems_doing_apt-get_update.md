---
title: "Problems doing: apt-get update"
date: 2005-12-19
forum: Desktop Environments
---

### Post by tgcUbuntu on 2005-12-19
I recently installed Ubuntu 5.10 and am having a problem when I do an update.
I use the command: sudo apt-get update
 
This is what I get:

ted@MainPC:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [19.4kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [586kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [2831B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [232kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2304kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [914kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [91.9kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [17.9kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [5088B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [8459B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [20.9kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [875B]
Fetched 4348kB in 30s (144kB/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems



Here is my /etc/apt/sources.list file:

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 


Any ideas what is causing the problem?
Thanks for any help you can give me.

Ted

---

