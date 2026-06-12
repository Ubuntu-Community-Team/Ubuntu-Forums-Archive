---
title: "After upgrade to 9.04"
date: 2009-04-26
forum: General Help
---

### Post by H4F on 2009-04-26
I get some packages missing.
tor
aria
skype
and other I might not know about.

apt-get install says :
Package * is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package aria has no installation candidate

from synaptics shows 
packagename and download size 1 byte

---

### Post by zvacet on 2009-04-26
Tor is not available on Ubuntu packages.For aria you have to enable universe repo in system>admin>software sources.For Skype you need [Medibuntu.]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by H4F on 2009-04-26
In software sources universe are selected.

```

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main universe restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main universe restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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
#deb http://md.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
#deb-src http://md.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main universe restricted multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed main universe restricted multiverse #Added by software-properties

## vidalia repostiros
# deb http://ppa.launchpad.net/adnarim/ubuntu hardy main # disabled on upgrade to jaunty
# deb-src http://ppa.launchpad.net/adnarim/ubuntu hardy main # disabled on upgrade to jaunty
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main universe restricted multiverse #Added by software-properties
## tor repository
deb http://mirror.noreply.org/pub/tor hardy main
deb-src http://mirror.noreply.org/pub/tor hardy main


```

---

### Post by zvacet on 2009-04-26
Try 

```
sudo apt-get update && sudo apt-get upgrade
```

If still no luck replace your source list with this one 

> #deb cdrom:[Ubuntu 8.10 _Jaunty Jackalope_ - Release i386 (20081029.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

## Medibuntu - Ubuntu 8.10 "jaunty jackalope"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

Save and close file and run 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by H4F on 2009-04-26
sorry to say no lack.
apt-get install aria:
Package aria is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package aria has no installation candidate


I used your source.list

---

### Post by zvacet on 2009-04-26
In Jaunty you have aria2.That can be reason why you have troubles with installing-I don´t use Jaunty but I find package [here]("http://packages.ubuntu.com/search?keywords=aria&searchon=names&suite=jaunty&section=all"),so I supose you can find it in synaptic.

---

### Post by H4F on 2009-04-27
Aria2 does not have GUI.
I end up getting deb from web.

---

