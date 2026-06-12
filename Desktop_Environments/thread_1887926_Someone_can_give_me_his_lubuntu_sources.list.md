---
title: "Someone can give me his lubuntu sources.list ?"
date: 2011-11-28
forum: Desktop Environments
---

### Post by Hauru927 on 2011-11-28
Hello,

I need a lubuntu sources.list, is there anyone can give me his ?

Thank you !

---

### Post by nothingspecial on 2011-11-28
Here you go


```
# deb cdrom:[Lubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

---

### Post by Hauru927 on 2011-11-28
Thank you :D

---

### Post by Elfy on 2011-11-30
More information here - [http://ubuntuforums.org/showthread.php?t=1887987](http://ubuntuforums.org/showthread.php?t=1887987). That thread is now closed - _please do not post duplicates_ - your issue is not any more important than anyone else's.

---

