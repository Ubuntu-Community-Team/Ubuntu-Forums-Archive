---
title: "problem w/ Synaptics Package Manager"
date: 2009-08-14
forum: Desktop Environments
---

### Post by benwizzi on 2009-08-14
Been using Ubuntu for a few days now. now my synaptics does not want to work properly and gives me this error sequence:
```

E: Type 'For' is not known on line 48 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```Here's the sources list file:
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu jaunty main

For Ubuntu Intrepid (8.10):

```

---

### Post by kerry_s on 2009-08-14
put a "#" in front of "For Ubuntu Intrepid (8.10):"

---

### Post by benwizzi on 2009-08-14
how do i change permissions to edit this. I've tried to follow the tutorial on the ubuntu site but the functions don't seem to work the way they're supposed to. I am using v9.04 btw.

---

### Post by john stiles on 2009-08-14
sudo gedit /file location/filename
password

---

### Post by kerry_s on 2009-08-14
> **benwizzi said:**
> how do i change permissions to edit this. I've tried to follow the tutorial on the ubuntu site but the functions don't seem to work the way they're supposed to. I am using v9.04 btw.

press> **alt+f2**
type> **gksudo gedit /etc/apt/sources.list**

---

### Post by benwizzi on 2009-08-14
Nevermind got it to work...ty both.

---

