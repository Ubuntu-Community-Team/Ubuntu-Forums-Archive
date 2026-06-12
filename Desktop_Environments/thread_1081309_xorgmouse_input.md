---
title: "xorg/mouse input"
date: 2009-02-26
forum: Desktop Environments
---

### Post by jmslew on 2009-02-26
i just finished installing ubuntu 8.10 via minimal install cd, activated the root account and ran:
```
sudo aptitude install xorg blackbox
```
followed by:
```
startx
```
and x starts and uses blackbox, but i can't use my mouse or touchpad. are there any other xorg related packages that i need to install for
1) mouse/touchpad input (i am using a usb logitech g9 laser mouse/gateway p7811fx touchpad), or
2) general functionality (as in typically used by most people) of xorg?

thanks in advance

---

### Post by SalahTr on 2010-01-08
Try :
```
dpkg-reconfigure xserver-xorg
```
For reconfiguring **X**
Here's tutorial [HowTo: Reconfigure X with &#8220;dpkg-reconfigure xserver-xorg&#8221;]("http://ubuntuforums.org/showthread.php?t=690760")

---

