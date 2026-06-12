---
title: "help with original /etc/apt/sources.list in 9.04"
date: 2009-04-29
forum: General Help
---

### Post by AndreiMe on 2009-04-29
can someone please post the original sources.list file after a fresh install of 9.04. i messed up the sources without intention and found out that i haven't created a security backup. please.

---

### Post by tricolorpoa on 2009-04-29
This is an working sources.list for Brasil mirrors

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://br.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://br.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://br.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://br.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://br.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://br.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://br.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://br.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://br.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
# deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu jaunty main # desabilitado na atualização para jaunty

```

---

### Post by AndreiMe on 2009-04-30
thanks alot you saved the day. nice to find someone to help you in the same day. thanks

---

