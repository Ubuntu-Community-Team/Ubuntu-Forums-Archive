---
title: "Ubuntu performing a little slower since shrinking root partition with gparted"
date: 2008-12-13
forum: General Help
---

### Post by diablo75 on 2008-12-13
I recently had to reinstall Windows (on my dual boot setup) and felt like expanding the size of the partition area that would be dedicated towards it, shrinking the Ubuntu side (don't worry, I've got a 1TB drive coming that Ubuntu will get to itself soon enough).  While I'm waiting, I've noticed that the system seems to boot a little slower since shrinking the partition.  The partition itself is only being used about 55% to 60% right now, so it's not close to full.  I know how data is basically written to an ext3 partition (everything spaced apart) as opposed to an NTFS partition (fill gaps with partial bits, resulting in fragmentation).  But I'm wondering how gparted has re-written the data to the partition since shrinking.  The original size of the partition was about 80 GB and it's now about 50.  Is it possible that gparted method for shrinking ext3 may have caused ubuntu to take a slight hit in performance?

---

### Post by CatKiller on 2008-12-13
Did you do anything to your swap partition?

---

### Post by diablo75 on 2008-12-13
Nope.  Swap partition was not touched.

Edit:  I just noticed a couple major typo's in the original post.  I shrank Ubuntu and expanded the Windows partition (actually deleted the windows partition and created a new one)

---

### Post by CatKiller on 2008-12-13
> **diablo75 said:**
> (actually deleted the windows partition and created a new one)

Is your swap partition referenced in /etc/fstab by UUID, or by /dev/sda*n*? I don't know for sure, but it's possible that deleting the Windows partition changed the numbers of the remaining partitions. UUIDs should remain unchanged (that's what they're for).

Does ```
sudo swapon -a
``` yield anything enlightening?

---

### Post by diablo75 on 2008-12-13
> **CatKiller said:**
> Is your swap partition referenced in /etc/fstab by UUID, or by /dev/sda*n*? I don't know for sure, but it's possible that deleting the Windows partition changed the numbers of the remaining partitions. UUIDs should remain unchanged (that's what they're for).

Does ```
sudo swapon -a
``` yield anything enlightening?

I get no output from that command after entering my password.  Just takes me back to a command line immediately.

However, doing a "swapon -s" (instead of -a) shows a swap partition on sda6 (which is the swap partition).

---

