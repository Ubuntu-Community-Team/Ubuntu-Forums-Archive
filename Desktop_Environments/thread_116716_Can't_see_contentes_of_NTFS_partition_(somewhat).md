---
title: "Can't see contentes of NTFS partition (somewhat)"
date: 2006-01-13
forum: Desktop Environments
---

### Post by JesCed on 2006-01-13
Hello, all.

I am a new linux user (I've more or less toyed around with it before, but am seriously into it now), and I'm posting in regards to a little problem I've found.

My computer is set up with dual WinXP/Ubuntu boot, with XP on an NTFS partition. After install, I conveniently found a link to my hda1 partition on my desktop. So far, everything OK. However, on trying to browse the hda1 partition, I get a message saying that the contents cannot be displayed due to insufficient permission. However, when I go to System | Administration | Drives, if I click on the hard drive, then the Partitions tab, hda1 and browse, I can see contents of the partition with no problem. I can even access the properties tab and click on the boxes to change partition properties, but I get a message saying that the changes can't be written because the drive is read-only.  :confused: 

Is there any way I can get the desktop link to work, or will I always have to go the way I've described?

I'd really appreciate your info on this

---

### Post by aysiu on 2006-01-13
See the fourth link of my signature.
NTFS will remain read-only, though.
If you want read/write, make a FAT32 partition.

---

### Post by JesCed on 2006-01-13
Thanks a lot... that did the trick. :D

---

