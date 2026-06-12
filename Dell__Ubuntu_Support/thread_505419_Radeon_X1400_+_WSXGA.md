---
title: "Radeon X1400 + WSXGA"
date: 2007-07-20
forum: Dell  Ubuntu Support
---

### Post by dimafogo on 2007-07-20
Hi all!

I've just installed Ubuntu 7.04 on my Inspiron 6400 (video - Radeon X1400, monitor - WSXGA 1680x1050). Th system offers me only one resolution namely 1400x1050.
I've installed xorg-driver-fgrlx and typed:
```
aticonfig --resolution=0,1680x1050,1400x1050
```
and got a fullscreen stretched image. It seems not be a typical "resolution change" (in Windows with resolution of 1680x1050 all is o.k., nothing is streched, only more pixels are available to show a picture).

How can I get a normal 1680x1050-resolution without stretching?


Best regards,
Dima

---

### Post by Paul S on 2007-07-26
Try editing your /etc/X11/xorg.conf file to remove the resolution line altogether.  Then, when you boot up, it should scan the monitors and pick the correct resolution by itself.  To check and change resolution while X is running, open a terminal and type "xrandr -q" to list the possible resolutions, and "xrandr -s 1680x1050" to set it to that.

HTH

---

### Post by Ek0nomik on 2007-07-26
> **dimafogo said:**
> Hi all!

I've just installed Ubuntu 7.04 on my Inspiron 6400 (video - Radeon X1400, monitor - WSXGA 1680x1050). Th system offers me only one resolution namely 1400x1050.
I've installed xorg-driver-fgrlx and typed:
```
aticonfig --resolution=0,1680x1050,1400x1050
```
and got a fullscreen stretched image. It seems not be a typical "resolution change" (in Windows with resolution of 1680x1050 all is o.k., nothing is streched, only more pixels are available to show a picture).

How can I get a normal 1680x1050-resolution without stretching?


Best regards,
Dima

Post your xorg.conf file;

```
cat /etc/X11/xorg.conf
```

Backup your xorg.conf file;

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

You can also try to run a command in the terminal to setup your resolutions;

```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

Use the spacebar to select options.

---

### Post by strabes on 2007-07-26
If the above methods don't help you (which they should) check the resolution link in my signature.

---

