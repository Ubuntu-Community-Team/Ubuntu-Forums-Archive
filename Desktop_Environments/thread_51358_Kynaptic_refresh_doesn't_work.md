---
title: "Kynaptic refresh doesn't work"
date: 2005-07-23
forum: Desktop Environments
---

### Post by gordonbp on 2005-07-23
I've tried the method at [http://kudos.berlios.de/kf/kisimlar/swmgmt.html#h2add](http://kudos.berlios.de/kf/kisimlar/swmgmt.html#h2add) to add new repositories, but all I get is lots of error messages as below (with differing urls)
--
Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
--

I also get this error message when trying to refresh using the standard sources.list file. It shows 33% from the CD rom, does nothing else, and gives me lots of these errors. What's going on?

---

### Post by Xian on 2005-07-23
I'm not fond of that source list, but it may not be an issue in your case.
Backup your current /etc/apt/sources.list and use mine instead.

Then try doing a '$ sudo apt-get update' session.

```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

##Security Mirrors
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backup Security Mirrors
#deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb http://kubuntu.org/hoary-kde341 hoary-updates main

##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by gordonbp on 2005-07-31
[QUOTE=Xian]I'm not fond of that source list, but it may not be an issue in your case.
Backup your current /etc/apt/sources.list and use mine instead.

Then try doing a '$ sudo apt-get update' session.

```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

##Security Mirrors
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backup Security Mirrors
#deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb http://kubuntu.org/hoary-kde341 hoary-updates main

##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```[/QUOTE]
 A very long story, but eventually it seems that my resolv.conf file had 192.168.1.1 as the nameserver. I changed it to my ISPs DNS and all is well!

---

