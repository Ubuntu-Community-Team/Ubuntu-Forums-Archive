---
title: "How to change the kubuntu progress meter when booting"
date: 2009-09-26
forum: Desktop Environments
---

### Post by bayousoft on 2009-09-26
I installed Jaunty Ubuntu then updated with Kubuntu.  That all went well.  I used kde for a couple weeks and found a couple bugs so I am sticking with gnome for now.  

Cosmetically, what controls the boot up progress meter?  I am seeing the Kubuntu progress meter and would like to switch it back to the Ubuntu progress meter.

This is purely a cosmetic request.

TIA

---

### Post by Docaltmed on 2009-09-27
I've been wondering the same thing.

---

### Post by Docaltmed on 2009-09-27
Hah! Figured it out. Go to Synaptic, and download an application called "startupmanager". It is in the Universe repository. After installing, go to System -> Administration -> StartUp Manager. Click on the "Appearance" tab. Near the bottom of that screen, you will see a drop-down menu for "usplash themes". One of those selections should be "usplash-theme-ubuntu". Click on that, then click the "Close" button. It will do a bunch of processing and then close down. Reboot, and you will see your Ubuntu boot screen re-installed.

It looks like StartUp Manager can control a lot of other GRUB options, but I haven't dug into it yet. I might not bother, messing with grub makes me nervous.

---

### Post by bayousoft on 2009-09-27
> **Docaltmed said:**
> Hah! Figured it out. Go to Synaptic, and download an application called "startupmanager". It is in the Universe repository. After installing, go to System -> Administration -> StartUp Manager. Click on the "Appearance" tab. Near the bottom of that screen, you will see a drop-down menu for "usplash themes". One of those selections should be "usplash-theme-ubuntu". Click on that, then click the "Close" button. It will do a bunch of processing and then close down. Reboot, and you will see your Ubuntu boot screen re-installed.

It looks like StartUp Manager can control a lot of other GRUB options, but I haven't dug into it yet. I might not bother, messing with grub makes me nervous.


Thanks!!! It worked.

---

