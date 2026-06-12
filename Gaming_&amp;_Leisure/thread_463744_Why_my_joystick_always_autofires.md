---
title: "Why my joystick always autofires???"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by fanhe on 2007-06-04
My ubuntu's version is 7.04.System can recognize my joystick,but it default aotufire,and I don't know how to cancel autofire.:(
If it always autofires,it can't use to play games!I think it's a big problem of driver for joystick.
How to cancel autofire?:(

---

### Post by hikaricore on 2007-06-04
Have you ever configured your joystick?
Please search around, there are many threads around here that could explain the process much better than I can.

---

### Post by fanhe on 2007-06-04
I find a package named xserver-xorg-input-joystick which I have installed,it describe:
X.Org X server -- joystick input driver
This package provides the driver for joysticks.
More information about X.Org can be found at: <URL:http://xorg.freedesktop.org> <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>
This module can be found as the module 'driver/xf86-input-joystick' at :pserver:anoncvs@cvs.freedesktop.org:/cvs/xorg 

-------------------------------------------------------------------------------------
I think it's  the driver for joysticks,but after I uninstall it,the system also recognize my joystick and I can test it through jstest /dev/imput/js0!
Why???Is not  the xserver-xorg-input-joystick the driver for joysticks?How can I uninstall the real driver for joysticks because I want to install new one?

---

### Post by fanhe on 2007-06-05
My god!Today I borrowed a Generic USB Joystick(My joystick is a Twin USB Joystick) from my classmate and tested in my ubuntu,amazed me!It didn't autofire!Why???:( My Twin USB Joystick didn't autofire in my windows xp!
I don't know whether it's a bug.I'm very disappointed!

---

### Post by hikaricore on 2007-06-05
Did you even read the replies in your thread?
It's probably not a bug, just a non configured joystick..

If you did search around and nothing you tried helped then I'm sorry.
But based on your response I can't tell that you even tried ANYTHING.

And as for it working in windows: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by fanhe on 2007-06-06
I had found around via google but found nothing can help me.

---

### Post by hikaricore on 2007-06-06
I meant to search around the forums for one of the many threads about joystick issues.

---

