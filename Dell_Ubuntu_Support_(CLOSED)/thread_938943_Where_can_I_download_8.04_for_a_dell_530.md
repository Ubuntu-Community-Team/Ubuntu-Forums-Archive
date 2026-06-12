---
title: "Where can I download 8.04 for a dell 530"
date: 2008-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by timgrant on 2008-10-05
Where can I download the tweaked version of 8.04 that will work on my 530?  I now know theres a problem with IDE and RAID, which I don't understand.......only that if I change it to RAID in the BIOS Vista won't work............AAAAaaagh!

---

### Post by fs3rp4 on 2008-10-05
> **timgrant said:**
> Where can I download the tweaked version of 8.04 that will work on my 530?  I now know theres a problem with IDE and RAID, which I don't understand.......only that if I change it to RAID in the BIOS Vista won't work............AAAAaaagh!

Probably here [http://ubuntuforums.org/showthread.php?t=762770](http://ubuntuforums.org/showthread.php?t=762770)

---

### Post by timgrant on 2008-10-05
That's great, thanks

---

### Post by gbrainin on 2008-10-05
Careful about using the Dell 8.04 ISO: It is a copy of the reinstall partition, meaning that if you run it, it will repartition and wipe your entire hard drive, replacing it with a factory-install Ubuntu.  That's fine if it's what you want, but if you want to keep Vista, you should install off the standard 8.04 image.  It won't have the DVD playback stuff, but then again neither does the Dell image.

As for your RAID/IDE issue, if you want to dual boot, you should leave the BIOS in IDE mode, and use the boot switch (all_generic_ide) solution.

---

