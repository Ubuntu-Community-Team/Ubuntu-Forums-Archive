---
title: "messed up apt sources"
date: 2005-10-28
forum: Desktop Environments
---

### Post by gonus on 2005-10-28
Ok, hello all. I am a new convert for Ubuntu. It totally rocks so far. I am trying to get packages such as dvd::rip etc to make my desktop pc a desktop pc. However editing the sources and stuff now I get jacked up errors and was wondering if any one can tell me how to fix it and how to add the right sources so I can get up to date programs.

---

### Post by jasutton on 2005-10-28
Can you post some specific error messages that you're getting?

---

### Post by manicka on 2005-10-28
Follow the instructions for breezy here

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by SpectralDesign on 2005-10-28
I tried the psychocats link yesterday and it changed my problem but did not alleviate it....

Eventually, I got it back to normal with is as my /etc/apt/sources.list
(note: I'm in Canada, and some of my sources are ca.*.*, if you're elsewhere try the local country code?!?)


deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by nolan43 on 2005-11-07
manicka
Just the things I needed, for a newbie that is. And it's because of this great community I'll have it all working before school next year.

Thanks

---

