---
title: "Initramfs+Busybox with new motherboard"
date: 2009-02-05
forum: General Help
---

### Post by Thomeduk on 2009-02-05
I have recently 'upgraded' my motherboard and system using a Gigabyte GA-EP45-DS3 board plus Nvidia GT9500 video card plus Intel E7300 CPU.  When trying to load UBUNTU v7 (previously installed with the earlier system) or v8, the process crashes with Initramfs and Busybox.:sad: The problem is clearly hardware related.  

My previous system used the same SATA HDDs as the upgrade, so the problem does not relate wholly on the use of SATA vs IDE.  Further neither board was RAID capable so the RAID 'solution' doesn't apply neither does the 'floppy' disk 'solution'.   

I have 'tried' many of the work arounds posted but without result.  many of the so called solu5t6ions seem like desperate measures to me :-).  Does anyone have any idea what the problem is and what can be done to overcome it?

---

### Post by Titan8990 on 2009-02-05
Try adding:

acpi=off noapic


to your kernel boot line, for both the install CD and actual boot of the installation.

---

