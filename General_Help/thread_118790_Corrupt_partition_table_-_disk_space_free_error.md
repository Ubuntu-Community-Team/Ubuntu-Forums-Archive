---
title: "Corrupt partition table - disk space free error"
date: 2006-01-17
forum: General Help
---

### Post by Borusa on 2006-01-17
I have a fairly typical setup - ext2 filesystem for a boot partition, swap and then a reiserfs partition with everything else. Recently, I had a system crash after which GRUB reported Error 17. Reasoning that the partition table was corrupt, I booted the install CD and used it to restore the table.

Everything's now fine, except for one thing - the reiserfs partition (/) is showing as nearly full (35GB or so). When I run filelight (either myself or sudo) it only finds 12GB, which I believe to be closer to the right amount. Is there any way to make it recalculate the disk free space? Or am I reduced to a backup-and-reformat?

---

### Post by Azion on 2006-01-17
I think a backup and reformat, would be best.
If you could backup the data on reiserfs, then format that partition and restore.
Shouldn't be too painful if you've another machine around

---

