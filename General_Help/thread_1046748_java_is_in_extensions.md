---
title: "java is in extensions"
date: 2009-01-21
forum: General Help
---

### Post by scoter on 2009-01-21
I'm pretty much a newby to Linux, BTW. my son wanted to play runescape on my ubuntu 8.10 installation.  Runescape said we needed java. I downloaded sun java, jre-6ull, the 64 bit and the regular one, too(both are .bin). I think I may have installed both. Anyway, finally, java console appeared in my fireFox extensions list, but not in the plug-ins, and Runescape still wants java. I couldn't find a plug-in folder for firefox. I'm thinking I should start over, but am not confident of the procedure to follow to get java working as a firefox plug-in.

---

### Post by taurus on 2009-01-21
Java is available from the repos.  Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and hit Return to accept it.  Once the installation is done, restart firefox.

---

### Post by scoter on 2009-01-22
thanks, taurus. I ran those lines, and after the 2nd command, I got this response:

Reading package lists...Done
Building dependency tree
Reading state information...Done
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package sun-java6-plugin has no installation candidate

---

### Post by taurus on 2009-01-22
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure you have enable universe & multiverse.  Go to the 3rd party tab and enable the repos from canonical too.  Click Close and close down synaptic.  Now, run those two commands from a terminal again.

---

### Post by scoter on 2009-01-22
I checked "About:plugins" in my firefox browser and found Java(TM) Platform SE 6 installed 7 times, but with different file names. one early one named npoji610.dll,  then the others were all together at the bottom of the list, and were all named like: npjava13.dll, npjava12.dll, and so on.

---

### Post by scoter on 2009-01-22
Did that. Got this response:
E: Could not get lock /var/liib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



Oh...I'm sorry about my last post concerning "About Plugins". that was inaccurate. I was looking at a different computer, got confused, sorry.

---

### Post by scoter on 2009-01-22
Ooops...forgot to close synaptics. Finally, i ran the commands properly, but got the same answer...package sun-java6-plugin not available.

Can I just download it from somewhere?

---

### Post by taurus on 2009-01-22
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by scoter on 2009-01-22
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
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
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
daddy@daddy-desktop:~$

---

