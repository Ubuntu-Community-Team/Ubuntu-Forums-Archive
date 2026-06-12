---
title: "fdisk deleted my lenovo recovery partition."
date: 2009-04-09
forum: General Help
---

### Post by suyash on 2009-04-09
I had Windows Vista on my lenovo laptop. Some time back I installed Ubuntu Studio on my laptop after removing Vista and had some free space. In this free space I installed Windows XP. I was happy with Ubuntu so I decided to remove XP. I used fdisk to delete the windows partition. However, this deleted all existing partitions except those used by ubuntu. 

I had my lenovo recovery primary boot partition /dev/sda1 which could install Vista again. This also got deleted. I badly want this partition back. In it's place fdisk shows free space exactly equal to the memory of deleted partition...

Help is appreciated

---

### Post by unutbu on 2009-04-09
The good news is that fdisk only changes your partition table -- stuff located in the first 512 bytes of your hard drive. It doesn't touch your data. So your data should still be intact.

> I used fdisk to delete the windows partition. However, this deleted all existing partitions except those used by ubuntu.

I am not sure I understand what you are saying here. Sometimes partitions are not visible, but that doesn't mean they are deleted. fdisk does not delete partitions unless explicitly told to do so.


Please boot into Ubuntu, open a terminal (Applications>Accessories>Terminal)
and type
```

sudo fdisk -l
```

This will show us your current partition table.

PS: You can recover your old partition table by installing the testdisk package and running
```

sudo testdisk
```

If you'd like some more detailed help on how to run testdisk, please post the output of "sudo fdisk -l" first so we have a better idea of your current setup.

---

