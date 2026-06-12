---
title: "Display randomly locks up"
date: 2006-06-01
forum: Desktop Environments
---

### Post by dguido on 2006-06-01
My displays is randomly locking up and I am forced to reboot.  Strangely, I can still move the mouse and login remotely over SSH.  I get the following message in my syslog at the time of lockup:

Jun  1 17:17:39 localhost kernel: [4303433.735000] NVRM: Xid (0001:00): 6, PE0000 046c 00ffffff 0000fde8 dfff0000 00ffffff

I am using an Nvidia card with the Nvidia binary drivers.  Does anyone know what the problem is?

---

### Post by ns2048 on 2006-06-09
Hello,

If your Nvidia card is on the AGP bus, try lowering the 'AGP Rate' value in your motherboard BIOS to '2x'. Many cards are unstable when the AGP Rate is set to '4x'.

You can check the current status of the AGP bus driver by looking at the contents of '/proc/driver/nvidia/agp/status'

Hope this helps.

--ns2048

---

### Post by dguido on 2006-06-13
I switched my cpu and mobo from an AMD 3000+ and KT880 chipset to an Intel 805 and Intel 865PE chipset.  I also upgraded the firmware on my video card.  Works now!

The firmware update makes the card think it never has the additional power plug in it though, kind of annoying.

---

