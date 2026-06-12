---
title: "Have an ATI 9600, which composite manager should I use?"
date: 2007-01-21
forum: Desktop Environments
---

### Post by Royle on 2007-01-21
I just got ubuntu 6.10 up and running, and would like to get some eye candy.  I've been reading about XGL and AIGLX, as well as Beryl and Compiz.  I can't really find a definitive answer for which one is better on a radeon 9600 (XT to be specific).  I don't know what drivers to use either, I just installed ubuntu so I guess I'm using the open source ones.  can someone help clear this up for me?  Thanks in advance for your help.

---

### Post by Viciou§ on 2007-01-21
ATGLX is built into the X server, while XGL runs ontop of X.
Running XGl might cause trouble if you want to play games and use other programs that need 3d-acceleration.

To get AIGLX to work you need the ati or radeon oss driver.
To get XGL to work properly I think you need the fglrx driver, ZIGLX doesn't support the fglrx driver.

running the oss drivers might make it impossible to make tv-out work correctly (I have an 9600Pro and can't get it to work) but fglrx drivers is a b*tch to install with direct rendering on.

So if you don't need TV-out I suggest you should try AIGLX

---

