---
title: "MBR problem"
date: 2006-06-13
forum: Desktop Environments
---

### Post by ampop on 2006-06-13
I resized my disk partitions, with partition magic.
After that I couldn't boot my Ubuntu, so I did a restore from a MBR-backup:
#dd if=MBR-backup of=/dev/hda count=1 bs=512

Now I can boot my Ubuntu system but I can't see a very important FAT32 partition. I thing that the FAT32 patition exists but it's not on table partition.
There is any way to the system read the real fisical partition and write it to the MBR?

Thank you.

---

### Post by jrd on 2006-06-13
Can you see it with gparted?

---

### Post by ampop on 2006-06-15
I solved my problem with TestDisk.
Very good.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

