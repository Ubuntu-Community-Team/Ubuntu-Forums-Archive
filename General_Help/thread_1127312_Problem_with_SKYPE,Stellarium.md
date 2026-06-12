---
title: "Problem with SKYPE,Stellarium"
date: 2009-04-16
forum: General Help
---

### Post by ravi_buz on 2009-04-16
My skype was working properly till few days ago but now when i start it , it just closes itself immediately .I tried to start it by terminal and the output was
Fatal: Cannot mix incompatible Qt libraries
Aborted

i am facing the same problem with stellarium also , so what to do

---

### Post by taurus on 2009-04-16
Did you upgrade qt recently?  You didn't mix repos in /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by ravi_buz on 2009-04-16
I dont think so , but here is the list 
[PHP]ravi@Ravi-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb http://download.virtualbox.org/virtualbox/debian hardy non-free
deb http://blognux.free.fr/ubuntu hardy main
deb-src http://blognux.free.fr/ubuntu hardy main
[/PHP]

---

### Post by taurus on 2009-04-16
Does it let you reinstall them after you have deleted those two programs?  Are those the only two programs that would not run?  Do you have another KDE app that you can test (k3b perhaps)?

---

### Post by ravi_buz on 2009-04-16
Yes i am having problem with those two only, and i can run k3b . I tried to uninstall and install skype but no change

---

