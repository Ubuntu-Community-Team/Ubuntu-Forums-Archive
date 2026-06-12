---
title: "Lost direct rendering, how to get it back?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by mr_cazorp on 2006-08-22
I'm on a ThinkPad T40, ATI Radeon Mobile whatever card. This morning I rebooted and encountered the deadly update, which killed my X server. I got X back running, but now I've lost all hardware acceleration. When I boot from Live CD I get it, but I can't seem to restore it when booting from HD. I even gave up and tried reinstalling Ubuntu from the Live CD but the installer crashes! Woo hoo!

Anyway - how can I restore my ATI drivers? I mean, to the standard, out-of-the-box, freshly installed state, nothing fancy like fglrx. There's a lot of threads on installing stuff but I have a feeling I need info on how to uninstall things as well. 

Thanks for any help anyone can provide...I just want my opengl back.

---

### Post by maniacmusician on 2006-08-22
well I think that when ubuntu detects an ATI card, it automatically loads a prebuilt fglrx driver. so you can either install that from the repos (i think its in there) or i guess you could use the default vesa driver.

---

### Post by mr_cazorp on 2006-08-23
Well that's the thing, I'm on vesa right now and it's not accelerated. I've tried installing the ATI driver and fglrx but whenever I set the driver to fglrx in xorg.conf, X won't run at all. When I set the driver to "ati" it works sometimes but is never accelerated. When I boot with the Live CD, the driver is "ati". 

I'm at a loss. I'll happily uninstall and reinstall anything to get it to work - the only thing I *don't* want to do is have to reinstall Ubuntu.

---

### Post by mr_cazorp on 2006-08-23
Fixed. I used Synaptic to remove all fglrx referencing packages. Then I did dpkg-reconfigure xserver-xorg to set up my xorg with the ati driver. Then, I reinstalled libgl1-mesa and libgl1-mesa-dri and whaddya know, hardware acceleration is back.

---

