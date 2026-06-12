---
title: "Wesnoth won't install on Ubuntu 12.04 64bit"
date: 2014-02-12
forum: Gaming &amp; Leisure
---

### Post by huwwevans on 2014-02-12
Greeting all, I am trying to install battle for wesnoth on my computer I get the following error in the terminal:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wesnoth : Depends: wesnoth-1.10 (>= 1:1.10.5-1~ubuntu10.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
I'm not sure how to fix this problem.  Any ideas will be welcome.  
Thanks,

---

### Post by mikewhatever on 2014-02-12
The error complains about the package from 10.04, so, unless you run 10.04, let us see your sources:
```

cat /etc/apt/sources.list

```

---

### Post by huwwevans on 2014-02-12
Sure,  This could be embarrassing though.  I've had so much trouble muddling through installations in the past.  

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to# newer versions of the distribution.


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
# deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) natty main
# deb-src [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) natty main
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) presice non-free
# deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) presice non-free
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise non-free
# deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise non-free




There you go.  I hope it means something to you I'm really not sure I recognise any of it appart from virtual box.

---

### Post by mastablasta on 2014-02-13
you are using old repos: 
> deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

 it seems they are interfeering with new.

---

