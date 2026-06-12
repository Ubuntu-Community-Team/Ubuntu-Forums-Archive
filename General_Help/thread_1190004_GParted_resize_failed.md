---
title: "GParted resize failed"
date: 2009-06-17
forum: General Help
---

### Post by Endolith on 2009-06-17
I tried to delete an existing partition and expand the main partition to take up the space, but it failed.  I used the Jaunty LiveCD version of GParted.  

> grow file system to fill the partition  00:00:00    ( ERROR )             [B][I]
resize2fs /dev/sda7[/I][/B]             [I]
resize2fs 1.41.4 (27-Jan-2009)
Please run 'e2fsck -f /dev/sda7' first.[/I]When I run this command manually, it reports no problems. When I run resize2fs, it gives the same error. ```
ubuntu@ubuntu:~$ sudo resize2fs -p /dev/sda7
resize2fs 1.41.4 (27-Jan-2009)
Please run 'e2fsck -f /dev/sda7' first.

ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda7
e2fsck 1.41.4 (27-Jan-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Jaunty: 665315/4340752 files (0.6% non-contiguous), 16571397/17464655 blocks

ubuntu@ubuntu:~$ sudo resize2fs -p /dev/sda7
resize2fs 1.41.4 (27-Jan-2009)
Please run 'e2fsck -f /dev/sda7' first.

```I tried with the GParted LiveCD as well and it does the same thing.

So my partition is resized, but the filesystem is not.  Should I be worried?

[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/373409](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/373409)

---

### Post by zvacet on 2009-06-17
Correct me if I'm wrong,but it is look like you are trying to reize extended partition ans add space to primary one.If that is a case then delete partition and then shrink extended one.That will make free space and you can add it to primary partition.

---

### Post by Endolith on 2009-06-17
> **zvacet said:**
> Correct me if I'm wrong,but it is look like you are trying to reize extended partition ans add space to primary one.If that is a case then delete partition and then shrink extended one.That will make free space and you can add it to primary partition.

They're both extended partitions, next to each other.  I deleted the smaller one and extended the end of the larger one to take up the space left behind.

---

### Post by zvacet on 2009-06-17
SO,everything is O.K. now?

---

### Post by Endolith on 2009-06-17
No.  The partition is bigger, but the filesystem is not.  I don't know why the resize command fails, and I don't want to ruin something by mounting it.

---

