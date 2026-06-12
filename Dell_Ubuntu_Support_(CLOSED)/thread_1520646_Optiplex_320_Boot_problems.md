---
title: "Optiplex 320 Boot problems"
date: 2010-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cabec on 2010-06-29
I was recently given two Dell Optiplex 320 computers (both missing their hdds) so i decided to install Ubuntu on them. The system was running on sata (the cables were still connected to the mobo when i opened it) but i only had an old ide drive laying around so i hooked it up. After installing 10.04 (32-bit) i made sure my boot sequence was set correctly (Pata drive first), and tried to boot. Alas, Ubuntu failed to boot and the "No boot device avaliable. Press F1 to try again or F2 for setup" error popped up. 

Right now i am running off a live usb and am able to view my Hard Drive and it's partitions. 

I am fairly new to Ubuntu and would greatly appreciate the help, thanks.

---

### Post by jig36 on 2011-01-19
i have this machine myself and i had someone burn the 10.10 disc and they burned it at the lowest speed possible and everything installed and booted just fine sounds like a bad burn,bad optical drive or a bad hard drive.

---

### Post by frotzed on 2011-01-19
It sounds like the previous HDD was a SATA, right?  So if you're now using a PATA drive and a PATA ribbon, I'm wondering if you need to make sure your BIOS is configured correctly

Is there a setting in BIOS that looks like a PATA vs. SATA choice?  Perhaps there's a setting to enable PATA? 

I have two Optiplex 320 PC's at the shop right now (but am writing this response from home), I'll have a look at the BIOS in the AM and give more info. on what I find -- if anything. :)

---

### Post by frotzed on 2011-01-20
I was mistaken, I have Optiplex 620s.  At any rate, in the BIOS I noticed that the PATA drives do indeed need to be enabled.  I also noticed that there as a PATA 0 and a PATA 1.  I'd make sure personally that your HDD is plugged into the correct port on the motherboard.

For instance, if your HDD is plugged into the PATA 0 port on the Motherboard, make sure that PATA 0 is enabled in the Bios and in the boot sequence.

---

