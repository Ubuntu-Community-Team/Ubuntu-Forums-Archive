---
title: "Ubuntu Breezy repositories"
date: 2005-10-18
forum: Desktop Environments
---

### Post by rado_london on 2005-10-18
Hi I read hundreds of posts of the broken breezy souces.list.I would be pleased if someone who has worrking apt-get to  show his full sources.list and to explain what can I download with it.I mean which tyes of packages
Thanks in advance:smile: :smile: :smile:

---

### Post by seldenthuis on 2005-10-18
Here's my (working) sources.list:

```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://nl.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://nl.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://nl.archive.ubuntu.com/ubuntu breezy universe
deb-src http://nl.archive.ubuntu.com/ubuntu breezy universe

deb http://nl.archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://nl.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb-src http://nl.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

With this you can download all the packages from the main, universe and multiverse repositories, if that's what you mean.

---

### Post by rado_london on 2005-10-18
thanks but can you explain me what are the main, universe and multiverse repositories because iam new to apt-get

---

### Post by Ampersand on 2005-10-18
Main is the packages officially supported by the Ubuntu developers, Universe contains packages that aren't officially supported and Multiverse contains packages that aren't open source (like flash, certain codecs &c).

---

### Post by rado_london on 2005-10-18
cheers fo the info.i changed my sources.list and now i can install everything:smile: :smile:

---

### Post by nix4me on 2005-10-18
Im still having problems.  I used the above sources and i get a gpg error and then when i select all the upgrades it tells me some can't be received.

Any ideas?

nix

---

