---
title: "wine"
date: 2005-12-15
forum: General Help
---

### Post by obe1kenobi on 2005-12-15
I installed the wine and xwine packages, but how do I use it?

Also does half life 2 and counter strike source work on ubuntu?

---

### Post by jon_z on 2005-12-15
right click on an *.exe file and choose open with wine.. depending on your system, hl2 should run nicely..  I had wine running on a rh9 machine and got hl working nicely.

---

### Post by obe1kenobi on 2005-12-15
thanks much

---

### Post by obe1kenobi on 2005-12-15
I am getting this error trying to install wine from WineHQ.  It seems to install from the normal repository, but I can't find the program or use it in the right-click on a .exe file.

> Package wine is not available, but is referred to by another package.  This may mean that the package is missing, has been obseleted , or is only available from another source
E: Package wine has no installation candidate

Here is my sources.list
> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

#wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

#opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

#OO2 final
#deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./


here is my /etc/apt/preferences

> 
Package: wine
Pin: release |=WineHQ APT Repository
Pin-Priority: 1000

 
I'm really confused, so any help would be great.  Thanks.

---

### Post by kaamos on 2005-12-15
Try:
```
sudo apt-get update
sudo apt-get install wine
winecfg
```
And post the output here. If the last command gives you a wine config window, your installation is ok. It might not show up in the "open with" menu so theres the option for custom command. Type "wine" there.

You can also run a program in terminal by navigating to the directory where the exe is at and using the command: "wine programname.exe" (like "wine hl2.exe")

---

### Post by obe1kenobi on 2005-12-15
thanks i got the wine configuration with that.  and now it shows up in the open with also.

Muchos Gracias

---

