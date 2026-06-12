---
title: "USB memory stick not recognized after installing Hardy"
date: 2009-01-18
forum: General Help
---

### Post by deronj on 2009-01-18
I just upgraded to Hardy Heron and my system no longer recognizes my USB memory stick when I plug it in. The light on the memory stick lights up but the file system is not automatically mounted. The mount always worked properly on my previous installation of Gutsy. (It's a Sony Vaio VGN FZ485U laptop). Thanks for your help.

---

### Post by taurus on 2009-01-18
Can you still mount it by hand from a terminal?  What's the output of this command?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by deronj on 2009-01-19
Thanks for your help.

sudo fdisk -l gives:

Disk /dev/sdb: 4009 MB, 4009754624 bytes
216 heads, 32 sectors/track, 1133 cylinders
Units = cylinders of 6912 * 512 = 3538944 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1134     3915759+   c  W95 FAT32 (LBA)

What -t argument do I use to manually mount this type of file system?

---

### Post by taurus on 2009-01-19
See if you can mount it by hand from a terminal.

```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by deronj on 2009-01-21
Yes. Thanks. I can manually mount it this way. 
At least this gets me access to the file system. But now the question I have is why doesn't it automatically mount?

---

