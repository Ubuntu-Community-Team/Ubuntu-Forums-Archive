---
title: "External Harddisk doesn't load all partitions"
date: 2006-08-27
forum: Desktop Environments
---

### Post by mbant on 2006-08-27
Hey there, I have a problem with my external USB harddisk. I'm running kubuntu (dapper).

The HDD is partitioned like this:
1: vfat partition
2: vfat partition
3: ext3 partition

When I plug it in, the first and third partition are automatically detected.
The second, however, isn't - I have to mount it manually. Of course, if I do that I bypass the kubuntu mechanisms and it doesn't pop up in the media section of konqueror, among with other inconveniences.

Any idea how I can teach my kubuntu to automatically detect all of my external harddisk partitions?

---

### Post by lagagnon on 2006-08-27
System, Administration, Disks, choose relevant hard disk, choose relevant partition, Enable, OK.

---

### Post by mbant on 2006-08-28
hi lagagnon, thanks for the quick response - but  I'm afraid it's not quite that easy. External (pluggable) harddisks don't have an 'enable' button (at least not on my machine :)). Besides, I want it to be auto-detected when I plug the disk in, not manually enable it afterwards (manually mounting works already).

Any ideas?

---

