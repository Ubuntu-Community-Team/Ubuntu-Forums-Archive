---
title: "connection between free / available memory in system monitor?"
date: 2009-02-04
forum: Desktop Environments
---

### Post by darthmob on 2009-02-04
hi there,
I have got a problem with my free disk space. the attachment shows what I mean.

the *available memory* converges at 0. at that point the system starts acting funny (I can not really blame it). firefox / nautilus bookmarks disappear and applications crash or don't react. I have started deleting files and in addition I moved some files over to my windows partition and created symlinks to save space. but I'm running out of files that I may delete.

**the problem is:** my ubuntu (7.10) constantly hogs filespace and I don't see where it happens. despite that there seems to be a lot of free space (2.5gig) that is not used.

**my question is now:** what is the connection between *free* and *available memory* and what can I do against that development despite getting a bigger hard disk?

thanks a lot in advance! ;)

---

### Post by kidders on 2009-02-05
Hi there,

The best way to explain the distinction between free & available memory is probably to use an example ...```
$ echo A > test
$ ls -l test
-rw-r--r-- 1 kidders kidders 2 2009-02-06 03:19 test
$ du -h test
4.0K	test
```
Imagine you have a 100k hard disk. Although "test" is only using 2 bytes, you would only have 96k of available space. Free & available space start out being approximately the same, but over time, the difference between them can become significant ... especially if you have small disks.

> **darthmob said:**
> the *available memory* converges at 0.You should not run a Linux system when it's out of disk space ... even for a few moments. To be honest, it's inadvisable to let it get even close. Doing so can cause long-term instability.

There are lots of places you can look for files you no longer need/want ... that topic is well covered here in the forums. One way of figuring out where all your disk space has gone is to use a disk space mapper (eg du, baobab, kdirstat, etc).

I hope that helps.

---

### Post by darthmob on 2009-02-08
your post did in fact help me a lot! :)

> Imagine you have a 100k hard disk. Although "test" is only using 2 bytes, you would only have 96k of available space. Free & available space start out being approximately the same, but over time, the difference between them can become significant ... especially if you have small disks. the blocksize being responsible for that difference sounds logical to me. I would not have expected it to be that much, though.

> One way of figuring out where all your disk space has gone is to use a disk space mapper (eg du, baobab, kdirstat, etc).
baobab was a nice recommendation! it helped me find 15gb of stuff I didn't need anymore.

PS: I know that it is not recommendable to run a system on no free space and I did not do it on purpose. but that problem is solved now! thank you very much!

---

### Post by kidders on 2009-02-08
No problem. :-)

---

### Post by dracozombie on 2009-08-02
> **darthmob said:**
> the blocksize being responsible for that difference sounds logical to me. I would not have expected it to be that much, though.

It's not so simple, it appears.  My first guess was that it was the excess space in the last block of each file.  I just noticed, however, that on my 500g drive, which contains 1,739 files, I have 203.8g free and 180.5g available as per System Monitor.  That's a 23.3g difference, which would mean an average 13.4m lost space per file.  I'm guessing that the size of one block on a 500g ext3 drive (formatted with Partition Editor) isn't anywhere near 13m, which would mean there's something else accounting for the gap between free/available space.

I emptied the trash, included .Trash-1000 and contents in the 1,739 figure just to be safe, and all files on the drive are non-hidden video clips.  I just installed the drive today, and the only thing I did before copying the video files to it was use it to temporarily hold another large group of files (which I deleted and verified weren't there anymore with df as well as looking in .Trash-1000 as root).  I also unmounted and ran fsck on the partition, and it came up clean.

Anyone have an answer?

---

### Post by kidders on 2009-08-02
> **dracozombie said:**
> Anyone have an answer?The difference is around 5% of the total filesystem volume, which is suspicious. Could reserved blocks account for the gap?

---

### Post by mcduck on 2009-08-03
> **kidders said:**
> The difference is around 5% of the total filesystem volume, which is suspicious. Could reserved blocks account for the gap?

Well, it most likely is. Since the amount of reserved blocks is 5%, and that disk space doesn't count as being available for normal users..

---

### Post by dracozombie on 2009-08-07
> **mcduck said:**
> Well, it most likely is. Since the amount of reserved blocks is 5%, and that disk space doesn't count as being available for normal users..

Just disabled reserve blocks with tune2fs and that was it:)

---

