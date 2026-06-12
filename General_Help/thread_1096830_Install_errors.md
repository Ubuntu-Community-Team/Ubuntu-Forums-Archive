---
title: "Install errors"
date: 2009-03-15
forum: General Help
---

### Post by grapestew on 2009-03-15
If I try to install anything, Virtual box or Wine I get this error 

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


When I try to update I get

 richard@richard-desktop:~$ sudo apt-get update
[sudo] password for richard: 
E: Type 'adding' is not known on line 55 in source list /etc/apt/sources.list
richard@richard-desktop:~$ sudo apt-get install -f
E: Type 'adding' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
richard@richard-desktop:~$ 


In the terminal window. I am very new to linux and my understanding is repository addrress change due to whoever has a server up and updates available at that address. But I am stuck :(

---

### Post by taurus on 2009-03-15
There is something wrong with your /etc/apt/sources.list, line 55.  Did you try to add something to it?

Open a terminal and edit /etc/apt/sources.list.  Remove line 55 (looks like the one that starts with the word **adding**).

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
If not sure, just post the whole content of your /etc/apt/sources.list.

---

### Post by grapestew on 2009-03-15
OK I think its at the bottom but not exactly sure here is the whole source.

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

adding repository
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 “Intrepid Ibex”

---

### Post by taurus on 2009-03-15
Remove the **adding repository** (second to last).  Also, remove the **-src** from the last line (for wine) because I assume you want to install wine.  Then save it.  Now run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by grapestew on 2009-03-15
Ok It downloaded everything and the updates seemed to work! Now do I have to run wine through terminal? or can I create an Icon for my desktop? sorry for my ignorance but its alot to learn! thank you for the fast replies!

---

### Post by taurus on 2009-03-15
Did you install wine?  You should see a menu in Applications -> Wine.  If not, reboot and check again.

Otherwise, you need to first run winecfg in a terminal to configure it first before you use it.

```
winecfg
```

---

### Post by d gnome on 2009-03-15
:KS hi..
     
     i am new to linux.. my ubuntu was workin wel.. but all of a sudden, the update manager doesn get launched, nor am i able to perform any admin tasks.when i try to install any update, it says"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

pl help:(:?:

---

### Post by taurus on 2009-03-15
> **d gnome said:**
> :KS hi..
     
     i am new to linux.. my ubuntu was workin wel.. but all of a sudden, the update manager doesn get launched, nor am i able to perform any admin tasks.when i try to install any update, it says"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

pl help:(:?:

Close update manager first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

