---
title: "mounting reiserfs"
date: 2005-09-24
forum: Desktop Environments
---

### Post by chortik on 2005-09-24
i have a raid array on my dell 1800. i formatted it for reiserfs with

*mkfs.reiserfs -b 8192 /dev/sdb1*

when i try to

*mount -t reiserfs /dev/sdb1 /array*

it fails with

*wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or other error*

however

*reiserfstune /dev/sdb1*

reports no problems. can you help?

---

### Post by GrumpySmurf on 2005-09-24
reiserfstune is used for tuning the ReiserFS - from the man page.

What is the output of:
```
sudo /sbin/sfdisk -l /dev/sdb
```

And what happens when you run:
```
sudo /sbin/fsck.reiserfs /dev/sdb1
```

---

### Post by chortik on 2005-09-24
here is the output

*sudo /sbin/sfdisk -l /dev/sdb*

```
Disk /dev/sdb: 121575 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+ 121574  121575- 976551156   83  Linux
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
```

*sudo /sbin/fsck.reiserfs /dev/sdb1*

```
###########
reiserfsck --check started at Sat Sep 24 15:35:20 2005
###########
Replaying journal..
No transactions found
Checking internal tree..finished
Comparing bitmaps..finished
Checking Semantic tree:
finished
No corruptions found
There are on the filesystem:
        Leaves 1
        Internal nodes 0
        Directories 1
        Other files 0
        Data block pointers 0 (0 of them are zero)
        Safe links 0
###########
reiserfsck finished at Sat Sep 24 15:35:38 2005
###########
```

---

### Post by GrumpySmurf on 2005-09-24
Have you tried mounting the filesystem again since running fsck?

Also, is there an entry in /etc/fstab for the new filesystem?

---

### Post by chortik on 2005-09-25
i've tried mounting again, got the same error.

the fstab entry is this:

```
/dev/sdb1       /array          reiserfs        defaults        0       1
```

---

### Post by chortik on 2005-09-26
ok, so the issue was that i was using 8k pages with reiserfs, but 4k pages in the kernel. there's probably an option to mount 8k pages, but i just reformatted with 4k pages and now it mounts. i'm missing 7% of the array to the FS structure.

thanks for your help

---

### Post by GrumpySmurf on 2005-09-26
Fortunately that was my next suggestion, really :). Glad you got it resolved.

---

### Post by chortik on 2005-09-26
it's annoying that i could not use larger blocks. this partition in on a raid array that will be used to store large files, so larger blocks make more sense.

---

