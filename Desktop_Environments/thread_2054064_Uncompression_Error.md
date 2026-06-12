---
title: "Uncompression Error"
date: 2012-09-06
forum: Desktop Environments
---

### Post by Yitzach on 2012-09-06
I just told my computer (12.04) to update, new Linux kernel among the updates. When I restarted it in recovery mode (like normal because normal hangs without progress), it said "Uncompression Error -- System halt" I tried the normal start up and I get the same message. I tried both of the memcheck, I think it what it is called, and it said something along the lines of insufficient memory. I have an option for previous versions of Linux. The first one was unhelpful as it looked like it had been modified. I don't think any of the others would be any better. But I do have Windows 7 on a separate partition. Windows reports 32,751MB of RAM and I can recover my files. Ext4 partition appears to be in one piece. I did look around to see what might cause it. They all sound like insufficient RAM. That doesn't sound right as Windows says I have 32GB of the stuff. Are there any other causes that can resolve this quickly as I don't have the time to be doing a system recovery with grad school and all?

I've been talking with other live people since this was originally posted. They suggest that I rebuild the kernel. I have a LiveCD on hand. What is the best way to attempt the trick and get it done in the least amount of time and trouble?

Computer specs:
MB: Gigabyte GA-Z68XP-UD3
GPU: GeForce GTX 460
RAM: 32 GB G.Skill
HDD: 3x Hitachi 500 GB in RAID 5
CPU: Intel i7-2600K OC at 3.9GHz
Successful install of Ubuntu 12.04 (840 GB) and Windows 7 (160 GB)

---

### Post by Yitzach on 2012-09-18
I borrowed a memtest+ disk from a friend. It went 2 passes and most of 3rd pass without error. I don't suppose the memtests listed in grub shares anything other than hardware, like say a kernel.

The last standing suggestion other than to reload the OS is to rebuild the kernel. I don't someone can give a good way to that? I do have the live boot on hand.

---

### Post by penreturns on 2012-09-20
what kernel are you using before it happen? what version of kernel did you upgrade? can you provide some detail?

---

### Post by Yitzach on 2012-10-06
I was using the standard issue kernel at the time. I updated to the next standard issue kernel. I can only count one other standard issue kernel since then. I have another Ubuntu machine that is running Lucid so I have a fairly good idea when Canonical sends out new standard issue kernel up dates. Could I give you version numbers? No I can't. I don't keep track of that stuff. I have other things to stuff in my head that have higher priority then the version number of my kernels because it usually works without interference.

---

### Post by Yitzach on 2012-10-06
I'm starting to think the RAID had an error. Not in the RAID table as Windows still works. I ran fsck from one of my boot options and I got this:

dev/mapper/isw_cdabhbifie_Disk2: Superblock last mount time is in the future. (by less than a day, probably due to the hardware clock being incorrectly set) FIXED.
dev/mapper/isw_cdabhbifie_Disk2: Duplicate or bad block in use!
dev/mapper/isw_cdabhbifie_Disk2: Multiply-claimed block(s) in inode 49414373: 197690375
dev/mapper/isw_cdabhbifie_Disk2: Multiply-claimed block(s) in inode 49414601: 197690375
dev/mapper/isw_cdabhbifie_Disk2: (There are 2 inodes containing multiply-claimed blocks.)

dev/mapper/isw_cdabhbifie_Disk2: File /home/user/.goutputstream-FHY9JM (inode #49414601, mod time Fri Aug 24 07:39:27 2012) has 1 multiply-claimed block(s), shared with 0 file(s):
dev/mapper/isw_cdabhbifie_Disk2: Multiply-claimed blocks already reassigned or cloned.

dev/mapper/isw_cdabhbifie_Disk2: 416940/50651136 files (0.2% non-contiguous), 14791976/202587648 blocks

I deleted the file in question and it didn't help. All it did was get rid the multiply-claimed error and double the incorrect last mounted error.

---

