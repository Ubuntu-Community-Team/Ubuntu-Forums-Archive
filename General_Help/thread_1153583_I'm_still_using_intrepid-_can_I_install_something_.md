---
title: "I'm still using intrepid- can I install something from jaunty repositories?"
date: 2009-05-08
forum: General Help
---

### Post by josephellengar on 2009-05-08
I'd like notify-osd but can't upgrade to jaunty yet for various reasons.  Can I switch to the jaunty repositories or something just to get that package?  I keep getting error 2 when I try to compile the package and the .deb that I found online was only for i386 systems and I'm on 64 bit.  Thanks!

---

### Post by vahnx on 2009-05-08
You can try if you like, see what happens. Here's my sources.lst file:

```

#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

#jaunty kde 3.5
deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu intrepid main

```

Make sure you backup your original, and comment out the extra ones I added. Then run **sudo apt-get update**

---

