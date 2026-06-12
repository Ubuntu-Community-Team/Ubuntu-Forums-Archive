---
title: "Partition table is not in disk order ,How to do it?"
date: 2009-06-03
forum: General Help
---

### Post by colau on 2009-06-03
Hi,
fdisk -l
```

/dev/sda7            6171        6833     5325516   83  Linux
/dev/sda8            8147        9729    12715416    b  W95 FAT32
/dev/sda9            6834        8146    10546641   83  Linux

Partition table entries are not in disk order

```
Is it possible to make partition table in disk order?

---

### Post by john.nicholls on 2009-06-04
Yes, it's possible, but you'd have to re=partition the whole disk. But why worry? My partition table is not in disk order, and it doesn't cause any problem.

---

### Post by dandnsmith on 2009-06-04
I'd agree with that - I too have a system which reports partitions out of order, but causes no problems otherwise.

If you do correct it, which is, in principle, possible with sfdisk, you may find some unintended consequences as a result of the new partition numbers/ids which couse some problems trying to sort them.

---

### Post by B-Con on 2009-06-05
I have this problem now, but it's not my fault.

I used the Windows 7 installer to delete a single partition, and the installer took the liberty of *renaming* every single partition after the deleted one so as to remove the gap in the partition names.

Did it ask me if I wanted to do this? No.

Such incredulous arrogance -- of course it should rewrite the MBR as it sees fit, after all, it's Windows.

Anyway, I liked my partition numbering the way I bloody had it before Windows took it for a joy ride. Any solutions on how to do this without deleting every partition manually would be appreciated.

I could always just copy the MBR to a file, edit it with a hex editor, and then write it back, but that sounds too annoying.


[edit]
Doh! It's simple:
- fdisk -l -- Note where each partition starts and ends
- Use fdisk to delete all unordered partitions
- Create new partitions using the partition starting/ending points from above, be sure to create them in order

This works because deleting a partition doesn't do anything but erase a marker in the MBR. You can delete and recreate the marker without effecting the partition itself.

---

