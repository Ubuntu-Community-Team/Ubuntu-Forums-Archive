---
title: "Messed Up Hard Drive"
date: 2009-06-09
forum: General Help
---

### Post by Boonzeet on 2009-06-09
I had a hard drive with 3 Partitions:
Filestorage: FAT32 10GB Logical  B:
Windows Vista: NTFS 132GB Primary  C:
Windows 7: NTFS 90GB Primary  A:

Windows decided to change the boot partition to C:. and I could not use C: due to a lack of BOOTMGR. I instaled Linux over it to try and fix it.

I want my system to boot A: now, how ould I do this?

---

### Post by Tipped OuT on 2009-06-09
Well, if you had the Windows Vista or XP installation disk, you could've jus booted up to recovery mode and automatically updated the BOOTMGR.

Since you installed Linux, all of the other operating systems available on your hard drive should of been added to the GRUB list. I hope you didn't just wipe your entire hard drive and installed Linux by mistake...

---

### Post by ManiacDan on 2009-06-09
Tipped Out is right, boot to the windows CD and perform a rescue install (or whatever they call it now).  XP on my dual boot at home actually boots to drive F, with the CD drive on E, the shared partition on D, and no mention of C.

-Dan

---

