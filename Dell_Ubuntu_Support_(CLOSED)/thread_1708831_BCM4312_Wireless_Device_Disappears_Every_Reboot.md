---
title: "BCM4312 Wireless Device Disappears Every Reboot"
date: 2011-03-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jpfulton on 2011-03-17
I've got a Dell XPS M1330 with a BCM4312 (that's a Broadcom wifi adapter) running Ubuntu 10.10. I've struggled to get the wifi working for a couple hours now and have read multiple posts but can't get it.

I'm currently using the b43 driver (I think it's the b43-fwcutter package) and not the STA driver (even though I think it's still installed according to Synaptics, it's not activated if I go to "Additional Drivers").

I can always get the wireless working if I do this:

sudo modprobe -r b43 ssb wl
sudo modprobe wl

But the minute I reboot the device disappears (If I go up to the network icon drop down thing in the status bar next to the clock)

When I run the modprobe command the wireless device suddenly comes to life and about a minute later successfully connects to my network.

Anything I can do to make this work the right way? Honestly at this point I'd be willing to just put those commands into some sort of bootup routine config file.

Thank you thank you

---

### Post by TBABill on 2011-03-17
```
gksudo gedit /etc/modules
``` and add wl to the end of the list, then save and restart.

---

### Post by mikewhatever on 2011-03-17
Make sure you don't have both the STA and B43 drivers installed, or in other words, bcmwl-kernel-source and b43-fwcutter packages, and if you do, remove one of them.

---

### Post by jpfulton on 2011-03-18
> **TBABill said:**
> ```
gksudo gedit /etc/modules
``` and add wl to the end of the list, then save and restart.

This did it. Thanks!!

---

