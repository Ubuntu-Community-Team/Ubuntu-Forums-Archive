---
title: "oneiric dev version : need to properly downgrade"
date: 2011-08-07
forum: Desktop Environments
---

### Post by arnaudj on 2011-08-07
Hello,

I upgraded to oneiric, a dev version.
(from 10.10 to 11.10)
Not very wise when not done on a vm, agreed.
Would you have a proper depot file for me to be able to downgrade properly?
(I've tried to do some recovery to natty, but... the kernel still specify oneiric, not natty, and many things are not behaving right. sometime no keyboard (being used by the network security keyring), most of the time no menu, ...)

Thank you a lot for your help
Feel free to ask me anything

actually, my source list looks like:

```
# deb cdrom:[Ubuntu 10.10S _Maverick Meerkat_ - Release i386]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.mirror.tn/ oneiric main restricted
deb-src http://ubuntu.mirror.tn/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.mirror.tn/ oneiric-updates main restricted
deb-src http://ubuntu.mirror.tn/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.mirror.tn/ oneiric universe
deb-src http://ubuntu.mirror.tn/ oneiric universe
deb http://ubuntu.mirror.tn/ oneiric-updates universe
deb-src http://ubuntu.mirror.tn/ oneiric-updates universe

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
deb http://ubuntu.mirror.tn/ oneiric-backports main restricted universe
deb-src http://ubuntu.mirror.tn/ oneiric-backports main restricted universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

deb http://ubuntu.mirror.tn/ oneiric-security main restricted
deb-src http://ubuntu.mirror.tn/ oneiric-security main restricted
deb http://ubuntu.mirror.tn/ oneiric-security universe
deb-src http://ubuntu.mirror.tn/ oneiric-security universe

## Medibuntu - Ubuntu 10.10 "maverick meerkat"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ natty free non-free # disabled on upgrade to natty
# deb-src http://packages.medibuntu.org/ natty free non-free # disabled on upgrade to natty

# Google software repository
# deb http://dl.google.com/linux/deb/ stable non-free # disabled on upgrade to natty

# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner
deb http://ubuntu.mirror.tn/ oneiric-proposed restricted main universe
```

---

### Post by oldos2er on 2011-08-08
There's no downgrade procedure, other than reinstalling 10.10.

---

