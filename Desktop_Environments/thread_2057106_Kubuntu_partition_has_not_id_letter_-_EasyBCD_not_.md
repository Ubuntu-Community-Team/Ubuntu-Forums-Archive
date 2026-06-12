---
title: "Kubuntu partition has not id letter - EasyBCD not seeing Kubuntu partition"
date: 2012-09-13
forum: Desktop Environments
---

### Post by tehno 2 on 2012-09-13
Hello there,

I installed Kubuntu 12.04 from ISO DVD and it was installed on a partition without ID letter "like C,D..." and was showing many options on reboot but Windows 7 was the last in the list. 
I tried to fix the issue using Easy BCD software which activated Windows 7 boot as default and Kubuntu exasperated from the boot option.
I checked my drives with several Partition programs and found Kubuntu still there. None of those programs was able to grant a letter to the partition and still I cannot launch the Kubuntu.

is there any way to fix this issue or I need to wipe the partition and have clean install.

Thanks

---

### Post by coffeecat on 2012-09-13
> **tehno 2 said:**
> I installed Kubuntu 12.04 from ISO DVD and it was installed on a partition without ID letter "like C,D..."

The "C:", "D:" way of counting partitions is a Windows-only convention, and it confuses drives with partitions. No other operating system uses this way of naming partitions.

> **tehno 2 said:**
>  and was showing many options on reboot but Windows 7 was the last in the list.

This was the "grub" menu, grub standing for GRand Unified Bootloader, the default bootloader in Ubuntu and most Linux distributions. It is possible to make Windows the default in grub without resorting to installing BCD. 
 
> **tehno 2 said:**
> I tried to fix the issue using Easy BCD software which activated Windows 7 boot as default and Kubuntu exasperated from the boot option.

You now need to configure EasyBCD to detect the Kubuntu installation. I have no experience of EsayBCD, and neither do many of the forum membership since grub is so versatile I would guess, but I'll edit your thread title in the hope that it will attract people with experience of EasyBCD.

One alternative would be to remove EasyBCD and go back to using grub, but that would involve a re-install of grub from the live CD. I suggest you don't attempt this without help

> **tehno 2 said:**
> I checked my drives with several Partition programs and found Kubuntu still there. None of those programs was able to grant a letter to the partition and still I cannot launch the Kubuntu.

See above for what I said about "drive" letters. Only Windows allocates drive letters for its own use within itself - they have no other meaning. I suggest you forget about drive letters when using any non-Windows OS.

---

