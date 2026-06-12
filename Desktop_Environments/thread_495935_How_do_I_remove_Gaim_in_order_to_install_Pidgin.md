---
title: "How do I remove Gaim in order to install Pidgin?"
date: 2007-07-08
forum: Desktop Environments
---

### Post by randell6564 on 2007-07-08
Hey folks!
I am trying to install pidgin via the [Ubuntu Feisty Guide]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Pidgin_2.0_.28former_GAIM.29") but after doing 
```
sudo dpkg -i pidgin_2.0.0-1_i386.deb
```
I get this Error message
> dpkg: regarding pidgin_2.0.2-1_i386.deb containing pidgin:
 pidgin conflicts with gaim
  gaim (version 1:2.0.0+beta6-1ubuntu4) is installed.
dpkg: error processing pidgin_2.0.2-1_i386.deb (--install):
 conflicting packages - not installing pidgin
Errors were encountered while processing:
 pidgin_2.0.2-1_i386.deb
THEN when I try and remove Gaim from synaptic, it wants to remove Ubuntu-Desktop as well!  How can I disable Gaim so that there are no conflicts with Pidgin?
Thanks!

---

### Post by smartboyathome on 2007-07-08
You can remove ubuntu-desktop safely without damaging your file system. ubuntu-desktop is just a meta-package for installing all the software included in ubuntu. If you ever want to upgrade, though, you may want to re-install ubuntu-desktop.

---

### Post by randell6564 on 2007-07-08
> **smartboyathome said:**
> You can remove ubuntu-desktop safely without damaging your file system. ubuntu-desktop is just a meta-package for installing all the software included in ubuntu. If you ever want to upgrade, though, you may want to re-install ubuntu-desktop.
AHHHH!  Thank you!  So if I "Mark for Complete Removal", can I reverse this process if Pidgin still will not work?
Thanks!

---

### Post by walkerk on 2007-07-08
```
sudo apt-get remove gaim ubuntu-desktop
```

then you can re-install ubuntu-desktop
```
sudo apt-get install ubuntu-desktop
```

---

### Post by biomega on 2007-07-13
But if I try to reinstall ubuntu-desktop it try to reinstall the gaim package :/

I'm new using apt, i've used all my life yum

---

### Post by randell6564 on 2007-07-13
> **walkerk said:**
> ```
sudo apt-get remove gaim ubuntu-desktop
```

then you can re-install ubuntu-desktop
```
sudo apt-get install ubuntu-desktop
```
Actually if you reinstall Ubuntu-desktop, it will reinstall Gaim as well.  I tryed it.

---

### Post by MystaMax on 2007-07-14
Hello,

Here are the two guides I found when trying to update to pidgin:

1. [forum post by DizzyTech]("http://ubuntuforums.org/showthread.php?p=2722318#post2722318")

2. [repo's @ debuntu.org]("http://www.debuntu.org/pidgin-2.0.0-deb-ubuntu-feisty-fawn")

I have two questions about these repositories. The first one did not contain [pidgin-libnotify]("http://www.debuntu.org/pidgin-libnotify-gaim-libnotify-for-pidgin-2.x"). But, the first one says:

> 
This repo is special, 'cause it has a GAIM transitional package to stay safe for Feisty updates.


Thats a good thing. The second repo mention doesn't state this.  Now, the second repo contains pidgin-libnotify; thats a good thing.

I asked these same questions at each site. I'll wait to hear back from each to see which route I go. **I'm looking for the easiest route for upgrades of Pidgin in the future**. I can deal with gaim until then, if need be.

---

