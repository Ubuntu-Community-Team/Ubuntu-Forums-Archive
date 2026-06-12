---
title: "Getting my pad to work"
date: 2007-05-23
forum: Gaming &amp; Leisure
---

### Post by Ludford on 2007-05-23
I have an xbox controller that I use to play games on my windows machine and I was woundering if I could get it working on my linux PC to use in some racing games like Vdrift.

I remember I had to install some drivers to get it to work in windows, but I can't seem to find them.

I'll try to find out the name of the driver, I think its something like XBCD

---

### Post by Naegling23 on 2007-05-23
have you tried plugging it in?  You would be shocked at what works.

I dont have an xbox controller, but my 2 logitechs, gravis, and nostromo n52 all worked out of the box.

---

### Post by adam0509 on 2007-05-23
[http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)

I think the right module for your pad is "xpad", but not sure...

EDIT :

$ modinfo xpad
filename:       /lib/modules/2.6.20-15-generic/kernel/drivers/usb/input/xpad.ko
license:        GPL
description:    driver for Xbox controllers
author:         Marko Friedemann <mfr@bmx-chemnitz.de>, Oliver Schwartz <Oliver.Schwartz@gmx.de>, Georg Lukas <georg@op-co.de>, Thomas Pedley <Gentoox@shallax.com>, Edgar Hucek <hostmaster@ed-soft.at>
srcversion:     7EC4E48313512193C8A772E
alias:          usb:v*p*d*dc*dsc*dp*icFFisc5Dip01*
alias:          usb:v*p*d*dc*dsc*dp*ic03isc00ip00*
alias:          usb:v*p*d*dc*dsc*dp*ic58isc42ip00*
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           debug:Debugging (ulong)

---

