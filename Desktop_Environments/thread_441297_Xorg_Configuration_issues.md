---
title: "Xorg Configuration issues"
date: 2007-05-12
forum: Desktop Environments
---

### Post by edge87 on 2007-05-12
Im running the lastest Kubuntu and I'm having problems getting the proper resolution out of my Xorg system. (1024*768)

Here is my Xorg.conf 

[http://rafb.net/p/x0WiCl94.html](http://rafb.net/p/x0WiCl94.html)

And here is an error log from /var/log/Xorg.0.log

[http://rafb.net/p/Wci4kA21.html](http://rafb.net/p/Wci4kA21.html)

Currently I have the nvidia driver working fine, its the legacy driver. Also the desktop loads up (kde) but the problem is it wont allow me to use 1024X768. I'm sure i've over looked a small detail that will cause this not to work for me. Anybody willing to help I would be thankful, thank you.

---

### Post by Kevinator on 2007-05-12
I'm not very sure, but it looks like the problem is this:

> (II) NVIDIA(0): DELL E773s: Using default hsync range of 31.50-37.90 kHz
(II) NVIDIA(0): DELL E773s: Using default vrefresh range of 50.00-70.00 Hz

...which is followed by a long string of modes that are discarded as invalid for the given values of hsync and vrefresh.

My guess is that you need to supply correct values for the hsync and vrefresh ranges. Maybe googling for your monitor model along with the terms 'hsync' and 'vrefresh', or maybe just 'xorg.conf' will tell you what the values should be.

---

