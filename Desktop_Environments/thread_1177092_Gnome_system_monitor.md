---
title: "Gnome system monitor"
date: 2009-06-03
forum: Desktop Environments
---

### Post by TMinh on 2009-06-03
Hi, Im a new member in forum, and Im Vietnamese, so sorry for my bad English.
I want to try Linux Mint, so I installed Mint 7 Gloria in a partition, and it used the same /home folder with Ubuntu. So I boot into Mint, everything gone fine. After that, I boot into Ubuntu GNOME session again, and I have a problem: In gnome system monitor, it display that my system is LinuxMint release 7 Gloria, not Ubuntu 9.04 Jaunty Jackalope! I remove Mint by deleting its partition, but the problem still happens! And I then foung another problem : softwares sources stops working in both gnome menu and synaptic!
Please help me fix these problems! Thank you very much!

---

### Post by x33a on 2009-06-03
post the output of 
```
uname -a
cat /etc/apt/sources.list
```

---

### Post by TMinh on 2009-06-03
Here...

```
Linux TM-PC 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```

and here...

```
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://vn.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://vn.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://vn.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://vn.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://vn.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://vn.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://vn.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://vn.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://vn.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://vn.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse

deb http://ppa.launchpad.net/ubuntu-vn/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ubuntu-vn/ppa/ubuntu jaunty main

deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main

deb http://ppa.launchpad.net/awn-testing/ubuntu jaunty main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu jaunty main

deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu jaunty main
```

---

### Post by x33a on 2009-06-03
The uname -a output is showing the distribution as ubuntu.

as for the updates issue, put a # in front of the first line of sources.list.

do
```
gksudo gedit /etc/apt/sources.list
```

then,

previously
> deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

after putting a #
> #deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted

then, save the file and do
```
sudo aptitude update
```

after this updates should be available to you.

---

### Post by TMinh on 2009-06-03
Thanks, but the problems still happen.
I still can't run Software Sources (Update and Synaptic run, but when I choose Repo in menu, nothing happens).
And in System Monitor, it still display "LinuxMint - Release 7 (Gloria)" (in System tab).

---

### Post by x33a on 2009-06-03
change the update servers and post the error you get while updating.

and post the output of sources.list again, after changing the server.

---

### Post by TMinh on 2009-06-04
> **x33a said:**
> change the update servers and post the error you get while updating.

and post the output of sources.list again, after changing the server.

No, I mean I just cant start the program named Software Sources in Gnome menu (and in Repo menu of Synaptic), and I can still use synaptic or apt to update, install etc as usual! I'm thinking of reinstall ubuntu to fix these problems.

---

