---
title: "screenreoslution cannot be fixed"
date: 2009-04-30
forum: Desktop Environments
---

### Post by newintolinux on 2009-04-30
As a newcomer to ubuntu i tried to install the latest distro on two laptops and experienced the same problem: The screen resolution is too low and everything looks very big.

The settings cannot be changed by me. If i install Kubuntu there is no rpoblem with my screenresolution and everything works fine.

I would like to switch to Ubuntu but i need to solve this problem. Can anyone help me to solve this?

---

### Post by AlecJ on 2009-04-30
You need to install the correct video card drivers. You don't say what type your computers have.

---

### Post by khelben1979 on 2009-04-30
Check what graphic card/chip there is before trying to install new drivers also:
```
sudo lspci | grep VGA
```

---

### Post by newintolinux on 2009-05-03
The laptop is a ASUS G1 with NVIDIA 9500M GS. I have tried to install the new drivers from nvidia but this also does not help.

---

### Post by blackened on 2009-05-03
[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") is a good place to start.

---

### Post by newintolinux on 2009-05-03
Today i spent some time again with uninstalling and installing Ubuntu 9.04 on the laptop. And the third time everything worked fine and i can set my screen resolution accordingly.

Thanks for the help

---

### Post by khelben1979 on 2009-05-03
> **newintolinux said:**
> Today i spent some time again with uninstalling and installing Ubuntu 9.04 on the laptop. And the third time everything worked fine and i can set my screen resolution accordingly.

Thanks for the help

Installing and uninstalling the whole Linux distribution should never be necessary. Hmm.. :-k But I guess this is the consequence when Windows users moves to Linux.

Glad that you got it working.

---

### Post by trentmc on 2009-05-03
I had this problem with a Toshiba laptop awhile ago.  I was able to do this by...


booting up off kubuntu live cd
copy the /etc/X11/xorg.conf to a usb flash drive 

boot back up into ubuntu
back up your current /etc/X11/xorg.conf
and replace it with the one you copied from kubuntu

... this worked for me

may be worth a try

- Trent

EDIT: just realized you have already fixed this .... anyway may be useful for someone else

---

### Post by blackened on 2009-05-03
> **khelben1979 said:**
> Installing and uninstalling the whole Linux distribution should never be necessary... 

Necessary no, sometimes easier than spending all the time it would take to diagnose, research, and repair that which you have torn up, absolutely. 

> ...Hmm.. :-k But I guess this is the consequence when Windows users moves to Linux...

True. Sad, but true. The bad part is that it's not always necessary to reinstall Windows either, but many do, both for the reasons I described above and just because they know it's a sure-fire way to fix their problem.

---

