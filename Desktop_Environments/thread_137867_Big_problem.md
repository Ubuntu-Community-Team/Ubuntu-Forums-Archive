---
title: "Big problem"
date: 2006-02-28
forum: Desktop Environments
---

### Post by tytanium0503 on 2006-02-28
hey everyone, I seem to be having a problem with my video card. When I boot up my system, my computer hangs on the "hotplug subsystem" message. I know my pci video card is the problem, so I've disabled it. The only problem is, I would like to be able to game on linux, but being unable to use my video card is going to bite. If you guys could help me at all with this, I'd appreciate it.

---

### Post by taurus on 2006-02-28
Can you share with us the brand and model of your video card?  Perhaps somebody here may have it running with Ubuntu...

---

### Post by tytanium0503 on 2006-02-28
oh yeah, I"m sorry. I have a dell dimension 2350 desktop system. A geforce fx 5200 pci card (yeah I know nothing extravagant). My chipset is intel 845g.

---

### Post by taurus on 2006-02-28
You have a nVidia video card and as far as I know, that is the most common video card that people use in Linux!  I have eVGA GeForce FX5600 in both of my machines and never have any problem with it.  If you want, you can edit /etc/X11/xorg.conf and use "nv" as your driver for now until you install "nvidia" driver for your machine...

---

