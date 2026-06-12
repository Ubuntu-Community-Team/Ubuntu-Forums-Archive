---
title: "default source lsit"
date: 2009-05-19
forum: General Help
---

### Post by hero1900 on 2009-05-19
hi all
could any one give me the default list of resources for Ubuntu 9.04

---

### Post by Concrete on 2009-05-19
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://rs.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://rs.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
```

Enjoy :)

---

