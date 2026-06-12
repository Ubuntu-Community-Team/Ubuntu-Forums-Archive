---
title: "Installing KDE desktop"
date: 2013-06-26
forum: Desktop Environments
---

### Post by oman.ispace on 2013-06-26
Hi

I am running Ubuntu 12.04 on 64-bit machine with Gnome 3.4.2

I am trying to install KDE using the following commands

```

sudo apt-get update
sudo apt-get install kubuntu-desktop

```

However here is what I am getting

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 kubuntu-desktop : Depends: xorg but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

[FONT=Century Gothic]**[COLOR="#FF0000"]_I checked xorg and it is installed in its latest version. Any idea why installing KDE installtion is failing ?_[/COLOR]**[/FONT]

Here is a listing of my /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://packages.mate-desktop.org/repo/ubuntu precise main
deb-src http://packages.mate-desktop.org/repo/ubuntu precise main

# R mirror
deb http://cran.ma.imperial.ac.uk/bin/linux/ubuntu precise/
```

---

### Post by zombifier25 on 2013-06-26
Try running these commands one at a time:
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update 
```
And try again.

---

### Post by dargaud on 2013-06-26
I think, but I'm not sure, that it's enough to install "kde-workspace"

---

### Post by oman.ispace on 2013-06-26
> **zombifier25 said:**
> Try running these commands one at a time:
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update 
```
And try again.

I tried but no luck

---

