---
title: "Help with Ubuntu 8.04 (Error 17)"
date: 2009-04-04
forum: General Help
---

### Post by hmmwhatsthisdo on 2009-04-04
Alright. First, let me say that I am VERY new to this, and have no idea what to do.
I have a _full_ install of Ubuntu 8.04 on my Kingston Traveldrive 8GB. I installed it via a live SD card version on a 1GB SD Card using Unetbootin. I have an ASUS P5Q motherboard, w/ a 320GB HDD running Vista Home Premium. After I installed Ubuntu onto the USB drive, I rebooted (vista still works fine), only to get "Error 17: Could not mount partition" or something like that. I know how to use Command Prompt in Vista, but not GRUB or BASH. what do I do to get ubuntu working? BTW, the 8GB drive had Ubuntu 8.04 on it once before. That crashed and burned after attempting to get internet access by installing a driver for the Atheros AR8121 built-in network card, and then installing 400 some-odd updates. I tried some of the help threads, but they make about as much sense as Chinese (I only speak & read English). Can Someone plz give me a hand?:confused::confused::confused::confused:

---

### Post by fabricator4 on 2009-04-05
Disconnect all other USB devices and plug the Kingston pen drive into the USB bus **on the back of the PC** and all on it's own.  Try a different port or bus.

Multiple USB devices, and front panel USB ports can sometimes be a little flaky.  Sometimes it's fine at the BIOS or Grub level, but fails later when the hardware is being scanned or drivers are loaded, which is what this sounds like.


Chris.

---

### Post by hmmwhatsthisdo on 2009-04-05
> **fabricator4 said:**
> Disconnect all other USB devices and plug the Kingston pen drive into the USB bus **on the back of the PC** and all on it's own.  Try a different port or bus.

Multiple USB devices, and front panel USB ports can sometimes be a little flaky.  Sometimes it's fine at the BIOS or Grub level, but fails later when the hardware is being scanned or drivers are loaded, which is what this sounds like.


Chris.
I have a USB keyboard, mouse, SD card w/ live Ubuntu 8.04, & (ipodless) ipod cable. Do I need to remove the keyboard & mouse? BTW, the "Front" USB port is actually from an internal SATA card reader, along w/ the SD Card, which I installed Ubuntu with.

---

### Post by fabricator4 on 2009-04-06
> **hmmwhatsthisdo said:**
> I have a USB keyboard, mouse, SD card w/ live Ubuntu 8.04, & (ipodless) ipod cable. Do I need to remove the keyboard & mouse? BTW, the "Front" USB port is actually from an internal SATA card reader, along w/ the SD Card, which I installed Ubuntu with.

You have to have a keyboard and mouse, so if you don't have PS2 devices you'll have to leave them in.  If you have four USB ports on the back of the PC move the keyboard and mouse over so they are on top of each other (plugged into the same header in other words) and plug the Kingston USB in next to them so it has a header on it's own.

I had another one today, where the keyboard and mouse plugged into the same header failed to work after boot.  PITA.  Try it and see how you go.

I haven't done anything with SATA USB ports at all, so I don't know if this is a good alternative for a USB boot device or not.

Chris

---

