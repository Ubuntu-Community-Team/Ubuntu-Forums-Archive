---
title: "Kubuntu 6.10 Edgy - /etc/sources.list"
date: 2008-08-14
forum: Desktop Environments
---

### Post by keenboy on 2008-08-14
I have a few kubuntu 6.10 desktop machines which run successfully as NIS clients. I am very happy with these machines and don't intend to upgrade them.

Can somebody tell me where I can find some working sources so that I can keep them up to date without having to upgrade the distribution?

My current sources which used to work are now producing 404 errors.

Any help is appreciated.

Thanks

---

### Post by null byte on 2008-08-14
My sources.list file from /etc/apt

```

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ro.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ro.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ro.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ro.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ro.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
## Wine, Ubuntu Hardy Heron (8.04):
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb-src http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main

```Dunno may be useful. I am running 8.04.

---

### Post by keenboy on 2008-08-14
Thanks but is there not a dedicated set of sources for kubuntu edgy?

I use 7.04 on my laptop and I experience no problems when updating with apt.

What drawbacks are there from having the 8.04 sources on a 6.10 distribution?

---

### Post by chris062689 on 2008-08-14
I believe it would essentially upgrade your system to a 8.04 distribution.
Edgy is no longer supported by the community.

---

### Post by keenboy on 2008-08-14
Surely this would only be the case if apt-get dist-upgrade was run?

If I run apt-get upgrade this should only bring in updated software packages, right?

---

### Post by chris062689 on 2008-08-14
If you change your sources to Hardy, of course there going to pull packages from the Hardy Repos.
I would suggest upgrading, Edgy is no longer supported.

---

