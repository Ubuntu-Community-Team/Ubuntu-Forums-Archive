---
title: "How did I get a SEC_TYPE for partition in blkid?"
date: 2009-06-03
forum: General Help
---

### Post by whoop on 2009-06-03
When I type:
```

sudo blkid

```
I see some partitions as TYPE="ext3" and some partitions as SEC_TYPE="ext2" TYPE="ext3".
SEC_TYPE stands for secondary type and could have something to do with that you can also mount it as another type?
But why is it for some ext3 partitions and not for others on my system (TYPE="ext3" is for all partitions. and some (f.i. /home) also have SEC_TYPE="ext2").
Could it mean that journalising is not enabled on these partitions, does it mean something else, can I change it?

---

### Post by unutbu on 2009-06-03
To check that the filesystem is ext3, run 
```

sudo tune2fs -l /dev/sdXY
```

(changing sdXY to the appropriate device name). If the filesystem is ext3, you will see something like

```
Filesystem features:      **has_journal** ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
```

It won't report "has_journal" if it is ext2. The existence of the journal is the only difference between ext2 and ext3.

PS. I don't know what SEC_TYPE means, or if it has any effect on Linux at all. I wish I did!

---

### Post by whoop on 2009-06-03
Thanks, the file system features include: has_journal.

I still wonder where this SEC_TYPE="ext2" comes from :-?

---

### Post by unutbu on 2009-06-03
According to this:
[http://osdir.com/ml/debian-bugs-dist/2009-05/msg02802.html](http://osdir.com/ml/debian-bugs-dist/2009-05/msg02802.html), and
[http://ubuntuforums.org/showthread.php?t=1077129](http://ubuntuforums.org/showthread.php?t=1077129)

mount uses libblkid to guess what type of filesystem exists inside a partition.
Presumably, mount is supposed to try the primary TYPE first, and if it fails, tries the SEC_TYPE.
According to the bug report, however, mount currently fails to try the SEC_TYPE if the primary TYPE fails.

---

