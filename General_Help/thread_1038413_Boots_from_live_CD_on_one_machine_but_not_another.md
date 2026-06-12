---
title: "Boots from live CD on one machine but not another"
date: 2009-01-12
forum: General Help
---

### Post by spindlhead on 2009-01-12
I'm brand new to ubuntu (and Linux) so please forgive my newbie language.  

I'm having trouble booting 8.10 in demo mode from a live CD on my old laptop .  The CD is a good burn. I tested in on my newer laptop (Toshiba U205) and it loaded just fine. 

The old laptop is a:
Toshiba Satellite A65-P126 
2.8GHz Celeron
60GB IDE HDD
768MB DDR SDRAM 
128kB l2 cache
ATI Mobility Radeon 7000 IGP (shared video memory)

Many thanks if anyone can help!

There is known physical damage on the hard drive.  I turn off the "quiet" and "splash" boot parameters when I try to load the demo.  The boot process seems to hang during a hard disk check.  Near the end of each boot attempt there are a number of errors that look like they're associated with disk sectors.  Sometimes it hangs after trying to "synchronize".  Sometimes I get a kernel panic.

Is there a way to suppress the disk check and hard disk mount during boot?  I was hoping to mount the disk after ubuntu loads, rescue any files to a usb stick, then repair the disk (mark bad sectors, fix MBR), all in demo mode, and finally do a hard disk install of ubuntu.

Many thanks if anyone can help!

---

### Post by spindlhead on 2009-01-12
One other datum.  I can boot DSL from a live CD on the old laptop.  My problem with DSL is that I can't get it to recognize or mount a USB drive.

---

### Post by mikewhatever on 2009-01-12
Ubuntu live cds are not made for rescuing purposes, but rather to test hardware prior to installing. In other words, it's like using a school bus for space traveling, use testdisk instead.


> **spindlhead said:**
> One other datum.  I can boot DSL from a live CD on the old laptop.  My problem with DSL is that I can't get it to recognize or mount a USB drive.

Lets not try solving all the problems at once, besides, this should go into 'Other OSs talk' section.

---

### Post by spindlhead on 2009-01-12
Thanks!  I'll try to find testdisk.  Still, any way to disable the disk check during boot?

> **mikewhatever said:**
> Lets not try solving all the problems at once, besides, this should go into 'Other OSs talk' section.

Oh, sorry, that's that's not what I was after.  It was just a data point that I was able to get one distro to load and not another.

---

### Post by J03y on 2009-01-12
Maybe going into the bios and booting from the cd manually could help.

---

