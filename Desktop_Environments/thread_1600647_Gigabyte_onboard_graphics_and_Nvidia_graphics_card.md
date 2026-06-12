---
title: "Gigabyte onboard graphics and Nvidia graphics card"
date: 2010-10-19
forum: Desktop Environments
---

### Post by tak360 on 2010-10-19
Hi everyone,

I have built a new machine and installed Ubuntu 10.04LTS Desktop 64bit. It has a Gigabyte H55M-UD2H motherboard with onboard graphics and an Nvidia 8400GS which I'd like to use for a second monitor.

It booted fine on install and displayed the desktop on my first (onboard graphics) monitor. The second (Nvidia) monitor displayed nothing. I updated all my packages then installed the Nvidia hardware driver (current recommended version) and rebooted when prompted. Now both screens are blank and I don't know what to do! I tried restarting again but same thing.

Any help would be greatly appreciated to get back to a terminal! And if you have advice on getting the Nvidia card to work alongside the onboard graphics that'd be awesome. Thank you :)

Tak

---

### Post by 3Miro on 2010-10-19
I don't think you can use two different video cards (as in Intel + Nvidia) with Linux graphical environment. I also don't think you can do that in any current SO (hybrid graphics for laptops is the closest thing, but even there, only one graphics is working at a time). I would really like to know if I am wrong, but I don't think so.

You Nvidia video card probably supports two monitors (it has two plugs) and from nvidia settings you may be able to set two monitors working on the same card. It is not a high end card, however, I got my laptop with Nvidia 9300 to work well in dual monitor with compiz cube and all.

Basically, your best bet is to disable the on-board video by unplugging the monitor (and maybe the bios). The plug both monitors on to the Nvidia card.

---

### Post by tak360 on 2010-10-22
> **3Miro said:**
> Basically, your best bet is to disable the on-board video by unplugging the monitor (and maybe the bios). The plug both monitors on to the Nvidia card.

Thanks 3Miro - I disabled the on-board graphics in BIOS and the machine  booted up a treat. I'm running my second monitor off the VGA port on the  Nvidia 8400GS but it's a bit fuzzy. It would be nice to have another  DVI port and I have a spare PCI-E slot. Would another Nvidia 8400GS  work?

Thanks again :smile:

---

### Post by 3Miro on 2010-10-22
Check with Nvidia and their forums, but my guess is yes. Xorg has trouble with different drivers, if you are using the same driver for both cards, it should work, however, extra settings may be required.

---

