---
title: "MPlayer in Breezy"
date: 2006-04-06
forum: Desktop Environments
---

### Post by TheEclypse on 2006-04-06
I am trying to install mozilla-mplayer, but when I search on synaptic, it finds mozilla-mplayer but says all the mplayer-X packages aren't installable.  Does anybody know what could be causing this ?

I have all of the binary repositories selected in synaptic, and a copy of my sources.list is below.

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://gb.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by TheEclypse on 2006-04-06
Problem solved, needed to add an extra entry to sources.list.

---

### Post by ahwei on 2006-04-09
[QUOTE=TheEclypse]Problem solved, needed to add an extra entry to sources.list.[/QUOTE]

May I know what is the extra entry to the sources.list? 

I have problem to install the MPlayer as well... much appreciated if  you can recall :D

---

### Post by TheEclypse on 2006-04-09
[QUOTE=ahwei]May I know what is the extra entry to the sources.list? 

I have problem to install the MPlayer as well... much appreciated if  you can recall :D[/QUOTE]


It was:

```
deb http://gb.archive.ubuntu.com/ubuntu breezy multiverse
```

---

### Post by jetix on 2006-04-09
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

