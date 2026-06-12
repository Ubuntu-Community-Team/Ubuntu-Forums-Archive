---
title: "Packages can not be verified"
date: 2006-01-06
forum: Desktop Environments
---

### Post by babuu on 2006-01-06
Hi,

Suddenly when installing any package, with apt-get or using synaptic, I get the message that the package can not be verified.

Anybody have any idea what can be causing this? 

My /etc/apt/sources.list looks like this:
--------------------------------
 deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe
multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
--------------------------------

/babuu

---

### Post by adwait on 2006-01-06
It doesn't really matter......you can go ahead and install the package even if it can't be verified.

---

### Post by babuu on 2006-01-07
Sure, the packages can be installed, but isn't the verification there for security? I might be installing "evil" packages.

---

### Post by adwait on 2006-01-08
Naah. All the packages in the Ubuntu repos can be assumed to be safe. The verification is for security yes, but if you are that paranoid, just import all the keys of the people who are authorised to sign the packages in the Ubuntu repos.

---

