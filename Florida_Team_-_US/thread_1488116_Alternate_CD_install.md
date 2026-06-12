---
title: "Alternate CD install"
date: 2010-05-19
forum: Florida Team - US
---

### Post by oldrunner55 on 2010-05-19
I recently purchased "Ubuntu Uleashed" and am wondering if the text install included on the DVD is the same as installing from the Alternate CD. I don't want GRUB in the MBR of my primary drive(WinXP Pro). I previously tried 10.04 and it pretty much trashed my MBR. The 10.04 install was on a second HD(160GB) and the only way to boot was with a "SuperGRUB" CD. I don't know if this is the proper forum to post to but after spending literally days searching through here to no avail this is a last resort.

---

### Post by mlsquad on 2010-05-21
Both installers install Ubuntu, with Grub.  The Windows boot loader will not boot any other operating system.  If you want to dual boot Windows and Linux you will need to use another boot loader, such as grub.
Grub is a pretty robust and stable boot loader.  The only problems I've ever seen with it is when you install Ubuntu using Wubi.  Ubuntu 9.10 started using Grub2, and as of 9.10 Wubi seems to have a hard time getting it to work right when trying to boot into Ubuntu, though getting into Windows still works as the computer is still ultimately using the Windows boot loader when the install is done through Wubi.

---

