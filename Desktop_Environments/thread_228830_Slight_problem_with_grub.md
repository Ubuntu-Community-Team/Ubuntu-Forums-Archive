---
title: "Slight problem with grub"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Saubazi on 2006-08-03
I bought myself a new SATA disk. I have already two IDE disks in the system. I messed around with the hardware for awhile and now I have DVDRW on primary master cable and the IDE HDs on secondary master and slave. So far so fine.

I disconnected both IDE disks and installed 64bit windows on the SATA disk but I am not able to integrate that into grub!?!

I have already a 32bit WinXP (which I later want to get rid of) on one of the IDE drives. 

Now the devices are showing as /dev/hda for DVDRW /dev/hdc for first IDE HD with Windows on it and then /dev/hdd for second IDE with Linux on it. SATA disk with 64bit WinXP would be now /dev/sda1

I have in grub root (hd0,0) for windows root (hd1,1) for Linux and now I tried entering similar entry to the old windows with (hd2,0) into it but unfortunately to no avail - funnily it will boot into the old winxp?!?!?

What should I enter in order to boot into the winXP 64bit on the SATA drive?

---

