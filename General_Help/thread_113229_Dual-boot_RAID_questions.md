---
title: "Dual-boot RAID questions"
date: 2006-01-05
forum: General Help
---

### Post by rick333 on 2006-01-05
I want to setup a dual boot Ubuntu/WinXP on an AMD64 dual core machine. I've installed vmlinuz-2.6.12-10-amd64-k8-smp. I have 3 SATA disk drives in the system, 1 80GB and 2x160GB. I plan to use the 80GB for my Linux /boot, swap, and /, and for the WinXP install, and would like to setup 2 RAID-1 partitions on my 160GB drives, one for /home and the other for a fat32 filesystem, to share data between Ubuntu and WinXP.

There are some complications. First, I'm not a Linux expert, so some of this stuff is a bit daunting. Second, WinXP/Pro supports sw RAID-0, but not sw RAID-1. Third, the Linux driver for the on board RAID controller, a Silicon Image 3114 SATARaid controller, is still beta, which makes me nervous. Don't want to lose my data. 

Looking for advice on whether and how to implement either of the following ideas:

1. Create a shared fat32 RAID-1 partition (mirrored) which would be accessed from WinXP via the Silicon Image 3114 RAID controller, and accessed from Ubuntu by md (software RAID)?

or...

2. Access the fat32 RAID-1 partition from both WinXP and Ubuntu via the 3114 controller? Is this advisable (due to the beta level of the Linux driver software)?

Thanks. I look forward to your responses.

Rick

---

