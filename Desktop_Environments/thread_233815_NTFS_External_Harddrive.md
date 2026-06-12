---
title: "NTFS External Harddrive"
date: 2006-08-10
forum: Desktop Environments
---

### Post by russoc4 on 2006-08-10
It seems that Linux has trouble writing to NTFS drives. What would be the easiest way for me to get my external harddrive working with ubuntu without having to reformat it into FAT32?

---

### Post by blueturtl on 2006-08-10
NTFS write support is experimental so if you value your data at all I would not suggest using NTFS on your hard-disk. Before you decide that this is a shortcoming, be notified that MS holds the spesifications of the file system closed, so no proper support can be written (and probably never will be). :( If you must use the disk with Windows, format it to FAT32. If not, there's really no good reason why you couldn't use one of the more advanced native systems such as EXT3 or ReiserFS on it. I'm sorry.

---

### Post by christhemonkey on 2006-08-10
NTFS support on linux has come a long way on linux recently,
the new ntfs-3g driver lets you read/write very reliably to NTFS drives.
Howto here:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by russoc4 on 2006-08-10
The easiest thing to do would be to format it to FAT32 after I move all my stuff of it. Can this be done in Ubuntu?

---

### Post by Martey on 2006-08-10
Yes. Check out gparted.

---

