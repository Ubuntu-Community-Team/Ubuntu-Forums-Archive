---
title: "Broken Packages"
date: 2009-07-07
forum: Desktop Environments
---

### Post by dontgetshocked on 2009-07-07
Here is my sources list.It shows a red button with a minus sign ion it for the upgrades instead of the arrow but wont let me do anything, it keeps telling me I have left over broken packages and I did use package manage to fix and it said it did, but it lied to me! I have done apt-get -f update and upgrade and the such with no success.


# added by the release upgrader
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)]/ jaunty main restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty main restricted
PROBLEM SOLVED.BY UNINSTALLING SOME SOFTWARE IT CLEARED UP. THANKS SO MUCH.

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by damis648 on 2009-07-07
What sort of error did 'apt-get install -f' give? Did you run it as root (ie as sudo)?
```
sudo apt-get install -f
```

---

### Post by dontgetshocked on 2009-07-07
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by dontgetshocked on 2009-07-07
I also used the code autoremove and here is the result,

Segmentation Fault

---

### Post by taurus on 2009-07-07
Go into System -> Administration -> Software Sources and uncheck the box for Cdrom.  Close it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dontgetshocked on 2009-07-07
Segmentation Fault when I use the upgrade .

---

### Post by taurus on 2009-07-07
```
lsb_release -a
```

---

### Post by dontgetshocked on 2009-07-07
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

---

### Post by taurus on 2009-07-07
Do you still get Segmentation Fault when you run the dist-upgrade option?

```
sudo apt-get dist-upgrade
```
I assume *sudo apt-get update* ran fine then.

---

### Post by dontgetshocked on 2009-07-07
Calculating upgrade... Failed
The following packages have unmet dependencies:
E: Unable to correct problems, you have held broken packages.

---

### Post by taurus on 2009-07-07
Can you post a screenshot of synaptic showing the broken packages (Edit -> _F_ix Broken Packages)?

---

### Post by dontgetshocked on 2009-07-07
Dont know how but am workin on sharing a folder on my drive.

---

