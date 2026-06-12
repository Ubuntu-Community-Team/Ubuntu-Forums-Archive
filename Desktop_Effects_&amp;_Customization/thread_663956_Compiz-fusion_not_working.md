---
title: "Compiz-fusion not working"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by speakeasy on 2008-01-10
Hey I'm new to the ubuntu game...
I'm trying to get compiz-fusion to work but I'm having a bit of trouble...
I used [https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion") to install compiz...
I'm pretty sure I have a 855gm intel graphics card... (dell 700m laptop)
when i go to system>preferences>compizconfig settings manager nothing happens...
and I cant turn on the desktop effects anymore...

also I'm running ubuntu 7.04 through a Wubi install... dont know if that changes anything...

---

### Post by Forlong on 2008-01-10
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by speakeasy on 2008-01-10
```
ii  compiz                                     0.5.2+git20070918-0ubuntu5~ppa1           OpenGL window and compositing manager
ii  compiz-core                                0.3.6-1ubuntu13                           OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070917-0ubuntu1~ppa1           Collection of extra plugins from OpenCompositing for C
ii  compiz-fusion-plugins-main                 0.5.2+git20070917-0ubuntu3~ppa1           Collection of plugins from OpenCompositing for Compiz
ii  compiz-gnome                               0.3.6-1ubuntu13                           OpenGL window and compositing manager - GNOME window d
ii  compiz-gtk                                 0.3.6-1ubuntu13                           OpenGL window and compositing manager - Gtk window dec
ii  compiz-plugins                             0.3.6-1ubuntu13                           OpenGL window and compositing manager - plugins
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1           Compiz configuration settings manager
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2~ppa1           Settings library for plugins - OpenCompositing Project
```

thanks

---

### Post by Forlong on 2008-01-10
You seem to have sources that interfere with one another.
Please post your /etc/apt/sources.list

---

### Post by speakeasy on 2008-01-10
```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main universe
```

I gues you dont need half that though,,,

---

### Post by Forlong on 2008-01-10
Hm... that's weird. How could you have compiz-gnome *and* compiz-gtk installed?!

See what I described [here](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) how to totally remove Compiz and then install it again.
(You can skip the part about adding the repository of course, since you already have it.)

Good luck, I'm going to bed now, so I hope this helps.

---

### Post by speakeasy on 2008-01-10
thanks man seems to be working...
fastest tech support anywhere!!!
thanks again...

---

