---
title: "Best way to remove ubuntu"
date: 2009-02-09
forum: General Help
---

### Post by Indyviews on 2009-02-09
What is the best and easiest way to remove Ubuntu and partitions from a hard drive in order to install Windows 2000?

I plan to reinstall Ubuntu afterwards.

---

### Post by LowSky on 2009-02-09
just use the live CD and use the partition editor, and delete the ubuntu partiions, then creat a new FAT32 partion to install Win2000 to

---

### Post by ajgreeny on 2009-02-09
You could also move and/or resize your ubuntu partitions with gparted on the liveCD, and not need to reinstall at all.  You will need to restore, and  fiddle a bit with grub and its menu and a lot will depend on your current setup, but it is possible.

However, if you have not personalised your ubuntu too much it could be just as simple to do what you are suggesting; this is just to make sure you're aware of all the possibilities.

---

### Post by binbash on 2009-02-09
Instead of removing ubuntu, resize the partitions via gparted live cd, install windows 2000 then re-install grub

---

