---
title: "2d-performance issues since dist-upgrade"
date: 2005-04-23
forum: Desktop Environments
---

### Post by mr.float on 2005-04-23
hi there,

i did a dist-upgrade 'bout a month ago from warty (which worked great) and since then my system feels all  slow, no matter what desktop i use:

- kdm (my co-admin is kde-user :): the background image takes about 10 secs to load. same when i log into gnome, changing the background is _very_ slow

- moving windows etc. leaves traces. you can see a new window build up in slow-motion. switching to another tab in firefox takes about half a second. even typing this post is painfull slow ...

i already removed the powernow-daemon, which didnt bring any recognizable speed improvment. 

system specs: duron 800, 256 mb, nvidia geforce fx 5200 (nvidia-driver), xorg

I'll attach some config and logs, maybe someone will find something suspicious, i cant (I had to cut the Xorg-log due to the limited atachment size):

---

### Post by fordfan753 on 2005-04-23
I'm by no means an expert...but I have installed several different operating systems (Windows 95, 98, 98se, 2000, XP Pro, Mandrake 10.1, Warty, Hoary, etc) and I have never got the same performance out of an upgrade as I have from a fresh install on a newly formatted partition. I know it may sound like a bit of a pain in the a***...but if possible just backup your files onto a CD, or even DVD (if you have a burner)..or even if you can put your important stuff onto another partition. Then put in the hoary disk and do a format and fresh install...in my experience it is always the best way. While there may be an upgrade option there it isn't always the best idea.

---

### Post by alastair on 2005-04-23
I don't think that's the full X log - but you have some unresolved symbols in the dri lib, so perhaps DRI (direct rendering) is disabled? 

Check : glxinfo

Also, if you are using the "nvidia" module, try changing to the open-source "nv" driver in the X config file and seeing if that helps.

---

### Post by mr.float on 2005-04-30
I'm back with a little update:

I've tried misc things, like using the 'nv' driver, enabling/disabling dri etc without any success

 I'm pretty certain my Xorg is somehow broken or misconfigured as 'top' shows it takes bout 10-20% cpu-time.

config & log:
[http://ezra.homedns.org/xorg.conf](http://ezra.homedns.org/xorg.conf)
[http://ezra.homedns.org/Xorg.0.log](http://ezra.homedns.org/Xorg.0.log)

glxinfo:
[http://ezra.homedns.org/glxinfo](http://ezra.homedns.org/glxinfo)

---

