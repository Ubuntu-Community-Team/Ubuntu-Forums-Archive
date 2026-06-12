---
title: "gparted, USB thumbs, not enough disk space"
date: 2010-06-21
forum: Desktop Environments
---

### Post by volobiz on 2010-06-21
Just so you know, with Ubuntu 8.04 LTS (which might still be an issue on later releases), I used gparted to detect my USB thumb drive and to try and reformat it from vfat into ext3. Well, I found a /dev/sda1 that said vfat, so I reformatted it. But Nautilus was still reporting vfat. As well, when I copied out about 1GB of data, eventually I started getting errors like not enough disk space and file exists.

Turns out that I had to switch also to /dev/sdb in gparted, find my vfat volume there as well, and reformat in gparted as ext3. Once I did that, not only the drive operate faster, but the file copy errors suddenly went away on 1GB of data. As well, Nautilus correctly identifies the new ext3 volume as ext3 instead of vfat.

---

