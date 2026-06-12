---
title: "How to specify which disk to mount in a script"
date: 2009-01-24
forum: General Help
---

### Post by Oldhacker on 2009-01-24
The Simple Backup program included works but leaves something to be desired - the inability to designate a partition of another physical disk as the target.

On this forum, the "tar" backup instructions posted by nunnst sounds like a better solution for backup.

I have two physical HD's, each with a number of partitions. When I manually mount the partition that I want to use from File Browser, it only shows up as /media/disk

To use this partition for backup (on the other physical HD) in a script, how do I specify which disk is being mounted and written to?

Thanks

---

### Post by septekin on 2009-01-24
I have named my ext3 backup drive using e2label and specify the disk by its name in the backup script.

---

