---
title: "[SOLVED] i cant install amsn by any way plez help"
date: 2007-09-19
forum: Desktop Environments
---

### Post by tropcky on 2007-09-19
hi  i cant install amsn by any way  look at thes pic  i am sorry   i cant install any thing not just amsn i got the same eror msg when i try to install any thing 
ooooh plez help

---

### Post by tropcky on 2007-09-19
oh ya and i got thes msg 2 when i tray to insatll it from the synaptic


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/tcltls_1.5.0-3~neto1-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/tcltls_1.5.0-3~neto1-3v1ubuntu0_i386.deb)
  302 Found

---

### Post by tropcky on 2007-09-19
plez help

---

### Post by tropcky on 2007-09-19
help plez

---

### Post by tropcky on 2007-09-20
any one plez i am totaly lost here realy need help

---

### Post by perce on 2007-09-20
it looks like you have a non-existing repository in your source.list. Please post your file /etc/apt/sources.list and I'll try to help you

---

### Post by tropcky on 2007-09-20
thank u so much man 
here it is 

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
#AUTOMATIX REPOS END

---

### Post by perce on 2007-09-20
The problem looks [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0. I suggest you to comment the two lines

 deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0

which means adding a # in front of them. They will then look like

# deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0
# deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy 3v1n0

To do hat open a terminal and type 

sudo gedit /etc/apt/source.list

to modify the file. Then save it, open synaptic an click the reload button.

---

### Post by seshomaru samma on 2007-09-20
you have added Edgy repositories to a Feisty machine - you might have some serious difficulties
did you use it to install Beryl?
you should follow perce's instructions

---

### Post by tropcky on 2007-09-20
oh man thank u soooooooooooo much it works now just fine thanks 2 u

---

