---
title: "Guide to Installing TimeVault on Ubuntu 64-bit"
date: 2009-06-10
forum: General Help
---

### Post by asuastrophysics on 2009-06-10
Welcome to asuastrophysics' how-to for installing TimeVault!

This guide will help you install TimeVault seamlessly on your Ubuntu 64 bit Machine.

[COLOR="Red"]**Requirements: Ubuntu 9.04 64 bit**[/COLOR]
(I have heard that this also works on Intrepid)

[COLOR="Black"]**_[SIZE="5"]Instructions:[/SIZE]_**[/COLOR]

**First, a few pre-requisites:**
   - getlibs (for running 32-bit installers on 64-bit machines)
   - python2.5 and a few python extensions
   - notification-daemon


1. In Terminal:
[COLOR="Red"]For Gnome Users:[/COLOR]
```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb && sudo gdebi-gtk getlibs-all.deb
```

[COLOR="Red"]For KDE Users:[/COLOR]
```
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb && sudo kpackagekit getlibs-all.deb
```

(All proceeding steps are the same for both environments) ;)

The installer will open. Hit "Install Package". When this is done, proceed to step 2.

2. In Terminal:
```
sudo apt-get install python2.5 python-gamin python python-pysqlite2 notification-daemon python-nautilus python2.5-dev python-gobject-dev meld
```

**Installing TimeVault**

1. In Terminal:
```
wget http://launchpad.net/timevault/trunk/0.1/+download/timevault_0.7.5-1_i386.deb && sudo dpkg -i --force-architecture timevault_0.7.5-1_i386.deb
```

Done! :popcorn:

Post and Questions / Comments below

---

### Post by linuxgrrl on 2009-08-29
Thanks for this!  I have Intrepid but the method seems to have worked.

---

### Post by bobbob1016 on 2009-09-08
For kde change the first line to:
wget [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb) && sudo kpackagekit getlibs-all.deb

---

### Post by asuastrophysics on 2009-09-30
> **bobbob1016 said:**
> For kde change the first line to:
wget [http://frozenfox.freehostia.com/cappy/getlibs-all.deb](http://frozenfox.freehostia.com/cappy/getlibs-all.deb) && sudo kpackagekit getlibs-all.deb

Thanks for your tip. I added this into the guide. :guitar:

---

### Post by akakingess on 2009-09-30
Just curious, if you have python 2.6 installed already, will that still work, or do I still need to install 2.5?

---

### Post by asuastrophysics on 2009-09-30
> **akakingess said:**
> Just curious, if you have python 2.6 installed already, will that still work, or do I still need to install 2.5?

that should work just fine. as long as it's at or later than python 2.5

---

### Post by akakingess on 2009-09-30
thanks for the quick reply, asuastrophysics!

---

### Post by garuhhh on 2009-10-01
I'm sorry to tell you that TimeVault doesn't work on my machine, and can't remember why. So i looked for an alternative, then i found [Back-in-Time]("http://backintime.le-web.org/download_page/"). 
It's based on "flyback" and "timevault", and it works on my system. It's deb is both for 32bit and 64bit. Or simply add the back-in-time repository, then install.

thanks for the guide, anyway. :D

---

### Post by asuastrophysics on 2009-10-04
> **garuhhh said:**
> I'm sorry to tell you that TimeVault doesn't work on my machine, and can't remember why. So i looked for an alternative, then i found [Back-in-Time]("http://backintime.le-web.org/download_page/"). 
It's based on "flyback" and "timevault", and it works on my system. It's deb is both for 32bit and 64bit. Or simply add the back-in-time repository, then install.

thanks for the guide, anyway. :D

That link seems to be dead :confused:
or not dead, but rather a link to a page that no longer has anything about back in time. :(

---

### Post by garuhhh on 2009-10-04
ooops.. i dunno what happend to the link. it was working when i tried it out. now it doesn't work.. anyway, just google for it, there might be existing links to download it.

---

### Post by StepNjump on 2011-03-23
What is the repository for this app? I tried to install it and it requires an old Python version. In Ubuntu 10.10 for netbook, we are at ver 2.6
Have you guys successfully installed it on Maverick 32bits?

---

### Post by garuhhh on 2011-03-23
When i was trying timevault i came across a newer and another solution which worked well for me. Try Back in Time.

[http://backintime.le-web.org/](http://backintime.le-web.org/)

Works in the same way as timevault..

---

