---
title: "NTFS under Linux or ext2/3 under Windows?"
date: 2009-03-28
forum: General Help
---

### Post by cfogelberg on 2009-03-28
Dear all,

I am configuring a new laptop to dual boot, and I want to have a /usr/share partition which stores data files that I will access in both Vista and Linux.

It seems to me that there are two options:
* Use NTFS on /usr/shared and mount it with the NTFS-3G drivers in Ubuntu
* Use ext3 and mount it with Ext2 IFS in Vista.

I plan to use Linux as the main OS, which makes me think I should use ext3 on /usr/shared, but if NTFS-3G is much more robust than Ext2 IFS then maybe I should use NTFS.

What do you think?

Thanks :)
Christo

---

### Post by sekinto on 2009-03-28
I'd go with NTFS, EXT2 IFS is picky and complains if you don't create the filesystem with some specific settings. Anyway, if you are only going to be accessing a few folders inside /usr/share you could just make those folders link to actual folders on your Vista partition where the data would be stored, but if you need to access many folders this would be inconvenient.

---

### Post by cfogelberg on 2009-03-31
I do want a separate partition for Vista programs and system files because I like being able to image the drive and easily restore it. Thanks for your suggestions though! :) xto

---

