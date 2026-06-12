---
title: "Problem installing Opera"
date: 2009-03-09
forum: General Help
---

### Post by zvacet on 2009-03-09
I never had problems installing Opera,but it looks like there is first time for all.When I try to install Opera I get the message 

> Failed to lock /var/cache/apt/archives/lock

I don´t know if there is connection,but when I click on network applet message is 

> Wired Network
device is unmanaged

I can surf the net with no problems.Anybody willing to help?!

---

### Post by sports fan Matt on 2009-03-09
Ive also had issues with installing Opera..so you arent alone

Both the qt4 debs fail to download (Opera 9 and 10 respectivelly).  I

---

### Post by UbuntuNerd on 2009-03-09
if you have more than one package manager working you can get that error, make sure you don't have synatic open or add/remove programs is not running in the background

---

### Post by zvacet on 2009-03-09
I just upgraded Hardy to Intrepid and this is first time that I have issues with Opera.I think I know why is that now.It look like I can not download anything and I have working network connection(obviously).Here is my source list

> # added by the release upgrader
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)]/ intrepid main restricted
# 
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


---

### Post by zvacet on 2009-03-09
@ **UbuntuNerd**

Thank for replay,but I make sure that I have just synaptic runing at the time.So,it is not that what gives me trouble.What confuses me is message 

> Wired Network
device is unmanaged 

witch will mean that I have some problems with net or network settings,but I use net fine as you can see.So only thing I can think of is message 

> E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I really need help on this one.

---

### Post by Crafty Kisses on 2009-03-09
Try running the following command:
```
sudo apt-get update
```
Then try re-installing.

---

### Post by UbuntuNerd on 2009-03-09
I found this link:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417")
it might be related to your problem, also check this other link:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1012963&page=4]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1012963&page=4")

---

### Post by zvacet on 2009-03-09
Everything is O.K. now.I shut down comp and start it after 1/2 of hour.All problems gone and I can download packages.Maybe server was down or something similar.

---

