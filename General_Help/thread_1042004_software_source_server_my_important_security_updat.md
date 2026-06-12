---
title: "software source server my important security updates"
date: 2009-01-17
forum: General Help
---

### Post by eAi-T0ky0 on 2009-01-17
[CENTER]Hi guys

  I think there was a problem with my server main maybe or something like that!!! Bec I was live in Egypt and now I live in anther country , And maybe the server main have changed!!!

I go to System>> Administration >> Software Sources and in ubuntu software Download from , select best server , And it select the server automatic

but it was nothing changed , I use ubuntu 8.04 hardy heron 

[IMG]http://img104.imageshack.us/img104/1214/screenshot2gl9.jpg[/IMG]

any idea please will helps me!!!![/CENTER]

---

### Post by plucky on 2009-01-17
What does ```
sudo apt-get update
``` from a terminal show you?

Please post output of ```
cat /etc/apt/sources.list
```


Good Luck

---

### Post by eAi-T0ky0 on 2009-01-17
ok I have update done , and this is output of cat /etc/apt/sources.list

```
Ezz@Ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.virginmedia.com/archive/ hardy main restricted
deb-src http://ubuntu.virginmedia.com/archive/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.virginmedia.com/archive/ hardy-updates main restricted
deb-src http://ubuntu.virginmedia.com/archive/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ubuntu.virginmedia.com/archive/ hardy universe
deb-src http://ubuntu.virginmedia.com/archive/ hardy universe
deb http://ubuntu.virginmedia.com/archive/ hardy-updates universe
deb-src http://ubuntu.virginmedia.com/archive/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.virginmedia.com/archive/ hardy multiverse
deb-src http://ubuntu.virginmedia.com/archive/ hardy multiverse
deb http://ubuntu.virginmedia.com/archive/ hardy-updates multiverse
deb-src http://ubuntu.virginmedia.com/archive/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://eg.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://eg.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ppa.launchpad.net/gilir/ubuntu hardy main universe
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ubuntu.virginmedia.com/archive/ hardy-security main restricted
deb-src http://ubuntu.virginmedia.com/archive/ hardy-security main restricted
deb http://ubuntu.virginmedia.com/archive/ hardy-security universe
deb-src http://ubuntu.virginmedia.com/archive/ hardy-security universe
deb http://ubuntu.virginmedia.com/archive/ hardy-security multiverse
deb-src http://ubuntu.virginmedia.com/archive/ hardy-security multiverse
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main
deb http://mirror.noreply.org/pub/tor hardy main
deb-src http://mirror.noreply.org/pub/tor hardy main
Ezz@Ubuntu:~$ 
```

---

### Post by plucky on 2009-01-17
> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse



Those two lines should not be in your sources.list.Use the **Software Sources GUI** and remove the dapper references or edit your sources.list file with ```
gksudo gedit /etc/apt/sources.list
``` and remove those two lines.


Did you get any errors when you "sudo apt-get update".Please post output.

Do the "sudo apt-get update" again after you have removed the two lines and post any error results.

---

### Post by eAi-T0ky0 on 2009-01-17
ok

---

### Post by eAi-T0ky0 on 2009-01-17
sorry , I just have get the idea now 

after you I removed the two lines

> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 

From

```
gksudo gedit /etc/apt/sources.list
```

[COLOR="Red"]there was now errors[/COLOR]


and it fix my problem , Thanks plucky for help


u the best


>

---

