---
title: "Can't install gmameui"
date: 2012-11-04
forum: Emulators
---

### Post by yvil on 2012-11-04
Hi,

I'm trying to install gmameui, a frontend for Mame.
Gmameui shows up in software center, but it doesn't find the package. I also tried to use apt-get install, but i get: 

```
E: Unable to locate package gmameui
```

from ```
cat /etc/apt/sources.list
```

i get:

```
# deb cdrom:[Xubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

Any clues anyone? :confused:
Thank you!

---

### Post by ibjsb4 on 2012-11-04
You see it in the software center?  Its not available for 12o4.

[http://packages.ubuntu.com/oneiric/gmameui](http://packages.ubuntu.com/oneiric/gmameui)

Unless you downloaded the PPA (which could be located in /sources.list.d), but that PPA is a source package.  Not a installable .deb.

[https://launchpad.net/ubuntu/precise/+package/gmameui](https://launchpad.net/ubuntu/precise/+package/gmameui)

---

