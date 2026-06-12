---
title: "Move of big file always stops at 4 GB"
date: 2008-12-04
forum: Desktop Environments
---

### Post by eber69 on 2008-12-04
I have an mpeg file of the size of 4.4 GB. I want to move it to an external disk but can't get it to load completely to that other disk. I'm running Ubuntu 8.04 and there seem to be a limit of some kind present. Any ideas what to do?
Cheers,
Martin

---

### Post by taurus on 2008-12-04
Bet your external harddrive is fat32/vfat filesystem!  It won't take filse bigger than 4GB so you need to reformat the harddrive to either ntfs or ext3.

```
sudo fdisk -l
```

---

### Post by blackened on 2008-12-04
Sounds like the drive is formatted as fat32 which has a maximum file size limit of 4GB. The only way to overcome this is to change the filesystem type of the external drive.

---

### Post by eber69 on 2008-12-04
Thanks, that's probably it. I have a lot of things on that disk and want to avoid reformating it. Could I split the file? I tried zipsplit commands but it seems, there's a limit of 2 GB to make a zip-file and zipsplit only takes zip files so it seemed a dead end.

---

### Post by Vantrax on 2008-12-04
use winRAR/tar to split the file into any size chunks you like.

---

### Post by eber69 on 2008-12-05
Ok, what would that command look like? I tried to check rar -help but nothing really sounds like split a file up.

---

### Post by eber69 on 2008-12-07
> **eber69 said:**
> Ok, what would that command look like? I tried to check rar -help but nothing really sounds like split a file up.

I found a geat guide for this:

[http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html)

---

### Post by stinger30au on 2008-12-07
you can install wine and izarc, it runs just fine

[www.izarc.org](www.izarc.org)

---

