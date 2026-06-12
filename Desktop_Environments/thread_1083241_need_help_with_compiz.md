---
title: "need help with compiz"
date: 2009-02-28
forum: Desktop Environments
---

### Post by pontifx on 2009-02-28
this has prolly been helped befor but i seem to not be able to find it....i built a junkyard pc and for some reason cant get compiz to work when i do the compiz check this is what comes up.... Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y
sketch@sketch-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

what am i doing wrong or not doing??? please help asasp

---

### Post by rushmobius on 2009-02-28
Go into System -> Administration -> Hardware Drivers and see if it lists the proprietary Nvidia driver for you to use. If it listed, you can select it and click Activate.

It will require you to reboot if I recall.

I don't think the open source nv driver supports compiz.

---

### Post by overdrank on 2009-02-28
I agree with rushmobius that the nv driver will not support compiz and I also believe that nvidia card is to old to support compiz as well.

---

### Post by pontifx on 2009-03-01
well it doesnt list any proprietary Nvidia drivers or any other for that matter so i guess im skreed huh?

---

### Post by benerivo on 2009-03-01
What nvidia card do you have? Try  lspci  in a terminal.

EDIT - Sorry, i've just seen that you've said it was the nv6 card.

---

### Post by WatchingThePain on 2009-03-01
I'm a noob but I think you can download the driver from the nvidia site and if it's not a debian package convert it with alien. It would be better to build it from source code if available. Or try this hehe..install envyng, relax and let it install the driver for you.

---

