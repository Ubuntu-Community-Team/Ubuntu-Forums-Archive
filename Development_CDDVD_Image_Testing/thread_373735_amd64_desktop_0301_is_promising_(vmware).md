---
title: "amd64 desktop 0301 is promising (vmware)"
date: 2007-03-01
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-03-01
UPDATE: same applies to 0301.1, which is probably Herd5

After almost one month of hiatus due to work pressure, I am back on amd64 desktop testing, always in VMware. I found that 27 and 28 Feb builds had some glitches:

27 Feb could not even format the vmdisk. Old bug regressing.

28 Feb had intermittent networking problems, still another old bug. I had to remove the virtual ethernet and readd it to make it work for a bit. No error logs were produced.

Today's 1st of March build seems **very ok**. I noticed a new tool upon installation, for migrating settings from older installations. Let's hope this does cause major problems. We are only one month away from release!

I feel that today's build is good enough to deserve my first attempt at real hardware installation (probably this weekend). My PC is the ideal worst-case scenario for installation (5 HDs, Asus P5B-VM, G965 chipset, Jmicron pata and feisty on the free space of a SATA disk with 3 existing ntfs partitions).

If feisty makes it on my PC I'll conclude that we are nearing RC1 :-)

---

