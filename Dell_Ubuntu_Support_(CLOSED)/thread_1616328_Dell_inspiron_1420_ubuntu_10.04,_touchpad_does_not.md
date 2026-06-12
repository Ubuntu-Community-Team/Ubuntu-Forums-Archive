---
title: "Dell inspiron 1420 ubuntu 10.04, touchpad does not double tap and drag"
date: 2010-11-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leawning on 2010-11-08
My touchpad can do scrolling and any other thing, except that it can't drag items by double tapping. What can i do? Thank you.

---

### Post by soulheart17 on 2010-11-08
go to this site and download touchpad apps 
[http://appnr.com/?search=touchpad](http://appnr.com/?search=touchpad)

hope it will work

---

### Post by flanker438 on 2010-12-24
having same problems with my dell 1420... google landed me here.

Does the above solution work?


Thanks

---

### Post by mikewhatever on 2010-12-25
Those are configuration utilities that should work if you have a synaptics touchpad, and if you don't, they'll most likely do nothing.

Edit: To find out whether or not your have the Synaptics touchpad, run the following command:
```
dmesg | grep -iE 'synaptic|touch|mouse'
```

If the output has nothing related to synaptics, then you most likely don't have one.

---

### Post by flanker438 on 2010-12-25
> **mikewhatever said:**
> Those are configuration utilities that should work if you have a synaptics touchpad, and if you don't, they'll most likely do nothing.

Edit: To find out whether or not your have the Synaptics touchpad, run the following command:
```
dmesg | grep -iE 'synaptic|touch|mouse'
```If the output has nothing related to synaptics, then you most likely don't have one.

This is the output that I got after executing above - (there is nothing sounding like 'synaptics' here)

[   0.445659] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.524783] mice: PS/2 mouse device common for all mice
[   13.639387] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[   13.884556] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[ 3800.527603] PM: suspend of drv:psmouse dev:serio1 complete after 423.317 msecs
[ 3804.722097] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input17
[ 3805.726429] generic-usb 0003:0A5C:4503.0004: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[10274.671528] PM: suspend of drv:psmouse dev:serio1 complete after 423.259 msecs
[10278.421762] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input21
[10279.434714] generic-usb 0003:0A5C:4503.0006: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[12093.447965] PM: suspend of drv:psmouse dev:serio1 complete after 423.694 msecs
[12096.932552] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input25
[12097.967112] generic-usb 0003:0A5C:4503.0008: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0

---

### Post by mikewhatever on 2010-12-25
Could it be that the Inspiron 1420 touchpad is not supposed to 'double tap and drag'?

---

### Post by flanker438 on 2010-12-25
I just changed Mouse's drag and drop, Double Click time out settings and  it seems to be working for me now, though not as smoothly as it used to  be in vista. (rare instances where one would find windows beter thn  linux :grin: ). It is manageable for me now.. :P

@mikewhatever - thnks to u for time :)

---

