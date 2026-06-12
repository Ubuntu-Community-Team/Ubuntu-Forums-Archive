---
title: "noatime and data=writeback"
date: 2009-05-23
forum: General Help
---

### Post by Regenweald on 2009-05-23
Do you use it ? I just changed my fstab to reflect noatime, I'm iffy about data=writeback though. I'll do anything to make this system faster :)

---

### Post by Xbehave on 2009-05-23
> **Regenweald said:**
> Do you use it ? I just changed my fstab to reflect noatime, I'm iffy about data=writeback though. I'll do anything to make this system faster :)

Use noatime on everything, and i will continue even when the once a day rule gets added, i have data=orderd on a few of my filesystems but i cant remember why. If you have the ram, try loading /tmp and /var/lock in tmpfs

---

### Post by Regenweald on 2009-05-23
Will research what you suggested.Thanks. Most of my data is static, i don't really see myself losing major stuff in a hypothetical crash so i'd prefer the maximum performance settings in ext4 and soon btrfs and tux3.

With noatime, Shiretoko memory usage seems to have dropped.

---

### Post by Regenweald on 2009-05-25
Was not really looking for support in this thread, but if it helps someone in here cool. I finally attempted data=writeback in fstab and rendered the xserver unusable and my filesystems read-only. No problem though, live cd + this tutorial:  [http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml) was all i needed. System is ridiculously responsive now :) At some point I'll have to put all this stuff together in a howto.

---

