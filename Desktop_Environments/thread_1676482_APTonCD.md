---
title: "APTonCD"
date: 2011-01-27
forum: Desktop Environments
---

### Post by onebir on 2011-01-27
This is in the repositories & I'd like to use it, but when I tried to install it this was the result:

```
onebir@onebir-laptop:~$ sudo apt-get install aptoncd
[sudo] password for onebir: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpackagekit-glib2-12 linux-headers-2.6.32-24
  libboost-program-options1.40.0 kdesudo libpackagekit-qt-12
  libakonadiprivate1 install-package linux-headers-2.6.32-24-generic
  python-packagekit packagekit gdebi-kde software-properties-kde kdepimlibs5
  update-manager-kde packagekit-backend-apt kdepimlibs-data python-kde4
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  aptoncd
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 268kB of archives.
After this operation, 2,007kB of additional disk space will be used.
[B]WARNING: The following packages cannot be authenticated!
  aptoncd[/B]
Install these packages without verification [y/N]? n
```I guess this shouldn't happen with packages available via the software center... perhaps this should be a bug report? 

But more generally, how can someone decided if a package is "safe"  to install in this?

Edit: just ran into the same warning trying to install wicd.

---

### Post by hhh on 2011-01-27
Post the contents of /etc/apt/sources.list here.

---

### Post by onebir on 2011-01-27
Thanks for the reply hhh.

Here's /etc/apt/sources.list :

```
#deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://il.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://il.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://il.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid universe
deb http://il.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://il.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://il.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://il.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by hhh on 2011-01-27
Sorry for the delay. Everything looks normal. aptoncd and wicd are from the "Universe" repository, which is not "officially" supported (hence the warning) but are safe to use...
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I assume you're seeing the warning because you are using apt-get to install and you wouldn't see that warning if you used the Software Center (I can't test that as I'm not currently on Ubuntu).

---

