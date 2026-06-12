---
title: "XBox controller in Hardy"
date: 2008-06-07
forum: Gaming &amp; Leisure
---

### Post by docPhunk on 2008-06-07
Alright i know there are a bunch of threads related to this but ive been through all of them and im still not sure what the issue is. Ive got a third party chinese xbox controller i converted to usb i also have a wired xbox 360 controller that is 100% working. from everything ive read the chinese controller should work its listed in the xpad.c, the controller comes up in my lsusb but jscalibrator wont pick it up. 

i followed this guide to compile the driver:
[https://help.ubuntu.com/community/Xbox360Controller]("https://help.ubuntu.com/community/Xbox360Controller")

im kinda a noob and this is my first post on the forum, any help would be much appreciated

Edit: ok now i have both joypads hooked up and i see my 360 controller and it works fine. jscalibrator show js0 (360 pad) ad js1 and js2...there are only 2 controllers hooked up. WHAT IS JS2!? the chinese controller does not respond in jscalibrator, neither does js2 ,whatever it is. lsmod shows the xpad module is loaded. best i can figure is that i may not have done the usb conversion properly, i didnt have the inline release on the controller (which is why i decided to mod it) but the wires ahead of the connection were the same as the guide showed for the adapter so im pretty sure it shouldn't make a difference. the controller has power for sure, the turbo button lights up. 

Can someone help me figure this out i wanna stomp my friends at street fighter.

---

### Post by docPhunk on 2008-06-09
bump

---

### Post by am28111 on 2008-07-19
I was also trying to get it to work, but could not figure it out. I realized that even without following the guide, the xbox 360 controller still shows up. 

Dsmeg shows:
```
usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 2519.618055] usb 4-2: configuration #1 chosen from 1 choice
[ 2519.908502] Registered led device: xpad0
[ 2519.908587] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2:1.0/input/input8
[ 2519.946325] usbcore: registered new interface driver xpad
[ 2519.946336] /build/buildd/linux-2.6.24/drivers/input/joystick/xpad.c: X-Box pad driver:v0.0.6

```

I'll have to play around with this more.

---

### Post by disturbedite on 2008-07-20
are you sure you even need to calibrate it? when i was using hardy & then intrepid i never needed to calibrate my xbox controller.
i just plugged it into a console controller usb hub & that was all i had to do.

---

