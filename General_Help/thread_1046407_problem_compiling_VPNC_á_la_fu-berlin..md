---
title: "problem compiling VPNC á la fu-berlin."
date: 2009-01-21
forum: General Help
---

### Post by amityak on 2009-01-21
So, I finally managed to get my wireless working on my new desktop and now I need my vpn client working in order to connect to my uni's network. I'm getting some hard time, and already forgot how did I manage to install it on my lappy.

So I've been following this HOWTO:

[http://www.zedat.fu-berlin.de/VPNC](http://www.zedat.fu-berlin.de/VPNC) --- Watch out thats in german!!

but basically what they say there is to :

1. making sure that my sources.list has a deb-src line
2. sudo apt-get install build-essential fakeroot
3. sudo apt-get install libssl-dev debhelper libgcrypt11-dev dpatch

till here everything went nice and easy. 

now the buggy part:

1. apt-get source vpnc

and i get:

```
jts@jts-desktop:~$ sudo apt-get source vpnc
[sudo] password for jts: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_hardy-backports_main_source_Sources - open (2 No such file or directory)

```

why is that happening ??

here is my sources.list file:

```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://ubuntu.beryl-project.org hardy main
```

afterwards I have also to edit the Makefile and uncomment some lines and the rebuild the package and install it... but first things first.

I would appreciate any helpful idea

Amit.

---

### Post by rauffenburg on 2009-01-21
Ok. you want to compile vpnc. But I do not quite get why. I can simply install it with synaptic; there is a vpnc package - without compiling anything. So why should I compile it from source? 

I am running Ubuntu 8.04

---

