---
title: "Format Drive with Ubuntu on it to NTFS"
date: 2009-03-29
forum: General Help
---

### Post by Sims12345 on 2009-03-29
Hi,

I have been running ubuntu for a while, but I want to try windows 7. I tried installing it and it wont let me because my drive is fromated as fat32 and it needs NTFS. I will not let me format from within the installer. I cant dual boot due to hardrive limitations...

So my question is how can I format my drive to NTFS within Ubuntu so I can install Win 7?

Thanks!

---

### Post by PhrankDaChickenGeek on 2009-03-29
How exactly are you setting this up? 
How many harddrives do you have - And partitions?

In the Vista installer, you can delete the partition you want to install to, and select the empty space, and it will automatically format it to NTFS. I assume Win7 does the same.

If you have Ubuntu installed on a separate partition, you can format other partitions with gparted:
```
sudo apt-get install gparted
```
And run with
```
gksudo gparted
```

BACKUP YOUR DATA BEFORE YOU DO ANY OF THIS! (Sorry, I just don't want you losing anything valuable)

---

