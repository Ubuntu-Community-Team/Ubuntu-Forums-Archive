---
title: "dual disk, dual boot, vista problems - non-system disk"
date: 2009-04-18
forum: General Help
---

### Post by bpalmer4 on 2009-04-18
I have just encountered a dual-disk, dual-boot problem that took a bit of head scratching to solve - so I thought I would share my problem and the solution.

Yesterday I purchased a solid state drive, which I installed so that it would come up as /dev/sda. Ye olde drive, that had windows vista on it would now be /dev/sdb. I also have two other hard drives, let's call them /dev/sdc and /dev/sdd to protect their anonymity. 

I installed the Jaunty Jackalope release candidate onto /dev/sda1, which then booted seamlessly. From my perspective this was an improvement on the beta release. So far so good.

But, when I tried to get to Vista from the grub menu at boot, I was rewarded with the cryptic message: Non-system disk, and the useless advice to press any key to reboot. Key pressing did nothing.

To cut a long story short, there was nothing wrong with grub. It turns out that the problem was caused by my BIOS. While linux faithfully reported windows was on /dev/sdb1, my BIOS listed that particular physical drive as the fourth in the boot order. When I made it the second hard drive in the boot order in the BIOS (to match being the second drive in Linux as /dev/sdb and in grub as hd1)- all was fixed.

---

