---
title: "how can I resize swap without live-cd"
date: 2005-12-07
forum: General Help
---

### Post by GoldBuggie on 2005-12-07
Is there a way to resize the swap without having to boot with a live-cd or something similar?

Maybe unmounting it and resizing it? Or will this crash the system do you think?

---

### Post by az on 2005-12-07
You cannot change the start of a partition.  You can change the end.

If your swap comes after your ext3 partition, you can:

1. boot the installer cd
2.  Get to the point where your hardware is detected
3.  CTRL-ALT-F2 to a shell
4.  Run parted and shrink your ext3 partition to make some free space before your swap.
5.  Delete your swap and recreate it starting at the earlier point.

Ex:
parted /dev/hda
print
resize 1
(enter numbers)
rm 5
mkfs
5
linux-swap
....

---

### Post by tonysathre on 2005-12-08
that would work, but just boot to the installer cd and when it gets to the partitioner, do it there

---

