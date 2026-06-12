---
title: "Soyo DYLM2284 doesn't do 1680x1050 on VGA."
date: 2009-05-08
forum: Desktop Environments
---

### Post by jimbolaya on 2009-05-08
I recently upgraded my desktop to Jaunty with "X.Org X Server 1.6.0" and got a new Soyo 22" monitor.  I have an ATI X1650 connected via AGP and I'm using the radeonhd driver since fglrx doesn't work with X.Org 1.6.

When plugged in via the RGB/VGA cable, even though xdpy and xorg.0.log insist the resolution is 1680x1050, the monitor says it's set to 1280x1024.  The edges of the desktop fall of the edge of the monitor.  If I use the DVI connection, it works fine.  I'd like to be able to use the VGA connector since it's attached to a KVM.

It works fine under Windows, via VGA, so it's not the connection per se.

Is this something I can fix using a modeline?  If so, how would I create one?

James

---

### Post by Kareeser on 2009-05-08
Yes, you *should* be able to fix this by introducing a modeline into your xorg.cong.

You can create one using the "cvt" utility.

```
cvt 1680 1050 60

will output...

# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

---

### Post by jimbolaya on 2009-05-10
Thanks.  I generated the modeline and put it in my xorg.conf, but it didn't seem to help at all.

Any other suggestions?

James

---

