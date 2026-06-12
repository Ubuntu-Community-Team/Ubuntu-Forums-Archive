---
title: "no more msttcorefonts?"
date: 2005-11-14
forum: Desktop Environments
---

### Post by garak on 2005-11-14
I can't find msttcorefonts package in synaptic :(

Added all repositories: universe, security, backports, even PLF.... but nothing!

I need MS fonts for web developing: any hint?

---

### Post by taurus on 2005-11-14
Have you tried "fonts" in the search field in synaptic to see what comes up?

---

### Post by kosmic on 2005-11-14
Are you sure ??
 
I'm looking to the Universe repositorie and it is there
 
msttcorefonts 1.1.11_all.deb
 
the link - [http://www.archive.ubuntu.com/ubuntu/pool/universe/m/msttcorefonts/msttcorefonts_1.1.11_all.deb]("http://www.archive.ubuntu.com/ubuntu/pool/universe/m/msttcorefonts/msttcorefonts_1.1.11_all.deb")

---

### Post by garak on 2005-11-14
here is my /etc/apt/sources.list

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://it.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://it.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://it.archive.ubuntu.com/ubuntu breezy universe
deb-src http://it.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

# PLF
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

``` 
If I try to search "fonts" in synaptic, I get a lot of other packages, but no msttcorefonts

---

### Post by No6 on 2005-11-14
There's your problem. The package is in the multiverse. just add multiverse to the end of the lines under ## team. e.g.

## team.
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe multiverse

---

### Post by garak on 2005-11-15
Thank you very much!
BTW, I also discovered that firefox now comes with a new search plugin, so I could find that msttcorefonts is in multiverse just using it! :)

---

