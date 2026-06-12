---
title: "external hard drive?"
date: 2008-12-04
forum: Desktop Environments
---

### Post by num on 2008-12-04
i got a seagate external hard drive and i want to move all my files off my current internal windows 1 tb drive to the external and then move all the files off the external to the redone internal one (linux). how can i do this?

i know that fat32 cannot handle large files and i know linux cannot read NTFS well. what can i do?

---

### Post by taurus on 2008-12-04
Fat32/vfat won't read anything larger 4GB but Linux can read and write to ntfs filesystem just fine with ntfs-3g.  Install ntfs-config and use it to mount your ntfs partition/drive.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

Meanwhile, windows can read/access ext3 filesystem with [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by num on 2008-12-04
how can i format my 1tb seagate external hard drive without erasing the hidden partition or the partition to restore to factory settings?

---

### Post by mitchroberts on 2008-12-04
Linux can read and write to ntfs file system   ):P
it should be able to read hidden partition 
too not sure never did that?

---

