---
title: "Kivio not supported?"
date: 2008-11-26
forum: Desktop Environments
---

### Post by SwedishWings on 2008-11-26
When i go to Applications -> Add/Remove... and search for Kivio i find the application, but is given the following notification:

> This application is provided by the Ubuntu community.
Kivio cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

I run a vanilla Ubuntu 8.04.

What is wrong here?

Thanks in advance,
Mike

---

### Post by nikgare on 2008-11-26
what does **sudo aptitude install kivio** do?

---

### Post by SwedishWings on 2008-11-26
> **nikgare said:**
> what does **sudo aptitude install kivio** do?

aptitude installs Kivio without complaints. But considering the warning text I'm hesitant to use it.

Should i just ignore the warning "Kivio cannot be installed on your computer type (i386)"? Is it a typo?

Thanks!

---

### Post by nikgare on 2008-11-26
When you use aptitude to install it, do you still get the error message?

---

### Post by SwedishWings on 2008-11-26
Please excuse my incomplete description of the problem. 

The attached image shows what i mean in more detail (gnome-app-install). 

The dialog box shows up when i try to select Kivio for installation. In other words, it's not possible to install Kivio this way.

However sudo aptitude install kivio works fine and don't complain at all. The application appears to be working, but i feel i can't trust it after this (unless someone can tell me what is going on here). 

Any advices would be most welcome!

/Mike

---

### Post by nikgare on 2008-11-26
I believe what you said, I need to find out if this is a package/stytem problem or a gnome-app-install problem.

Can you post your /etc/apt/sources.list file and the oupput from **uname -m**

---

### Post by SwedishWings on 2008-11-27
> **nikgare said:**
> I believe what you said, I need to find out if this is a package/stytem problem or a gnome-app-install problem.

Can you post your /etc/apt/sources.list file and the oupput from **uname -m**

Thanks for your effort. Here it goes:

```
mike@lap-ubuntu:~$ uname -m
i686
```
```
mike@lap-ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ph.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ph.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ph.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ph.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ph.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ph.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ph.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main

```

---

### Post by nikgare on 2008-11-27
When you try to install kivio via the command line: **sudo aptitude install kivio**
do you get the same error message, another message, no message?

---

### Post by SwedishWings on 2008-11-27
> **nikgare said:**
> When you try to install kivio via the command line: **sudo aptitude install kivio**
do you get the same error message, another message, no message?

**sudo aptitude install kivio** installs successfully without warning or errors.

The problem only relates to **gnome-app-install**

If you run **gnome-app-install**, can you actually install Kivio, or do you get the same message as I?

Thanks,

Mike

---

### Post by nikgare on 2008-11-27
I managed to install kivio via gnomeappinstall without erors, but I run 64 bit Ubuntu!

This is proly a bug in gnomeappinstall, could you submit the bug in launchpad?

---

### Post by SwedishWings on 2008-11-28
Ok, I will try to do that, though i never reported one before.

Thanks for your help!

/Mike

EDIT: reported: [https://bugs.launchpad.net/ubuntu/+source/koffice/+bug/303039](https://bugs.launchpad.net/ubuntu/+source/koffice/+bug/303039)

---

