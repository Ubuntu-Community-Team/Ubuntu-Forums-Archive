---
title: "Persistent names for removable drives"
date: 2007-07-08
forum: Desktop Environments
---

### Post by LeeM on 2007-07-08
I am trying to give persistent names to my removable drives. Many threads in this forum refer to
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)
but my system (Feisty) seems to have a different naming scheme. The document says to execute
udevinfo -a -p /sys/block/sda

and shows (trimmed) results like 
looking at device '/block/sda':
    KERNEL=="sda"
    SUBSYSTEM=="block"
    SYSFS{stat}=="  128535     2246  2788977   766188    73998   317300  3132216  5735004        0   516516  6503316"
    SYSFS{size}=="234441648"
    SYSFS{removable}=="0"
    SYSFS{range}=="16"
    SYSFS{dev}=="8:0"
 
but when I do it, I get (trimmed):
looking at device '/block/sda':
    KERNEL=="sda"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{stat}=="   64162     7578  1367398   372076    67446    31595  1022648   872568        0   184824  1244644"
    ATTR{size}=="390721968"
    ATTR{removable}=="0"
    ATTR{range}=="16"
    ATTR{dev}=="8:0"

so among other things, the nomenclature seems to have changed from "SYSFS" to "ATTR". Is this true, or am I missing something?

Also, when I look at a device (e.g., sda5) under a Parent device (sda), the nomenclature is "ATTRS". 

Help!

---

### Post by coffeecat on 2007-07-09
Why not just label the partitions? I do this and my external drives are always automounted with the same name. Despite its title, [this link]("http://doc.gwos.org/index.php/Understanding_fstab") has some useful information on labelling partitions - if you need it. It's about half way down. The author describes the use of mtools to label FAT partitions but I read somewhere else that it's not possible. Whatever - I use Windows to (re)label FAT partitions and e2label for ext3 ones.

---

### Post by Gwasanaethau on 2007-08-06
> **coffeecat said:**
> Why not just label the partitions? I do this and my external drives are always automounted with the same name. Despite its title, [this link]("http://doc.gwos.org/index.php/Understanding_fstab") has some useful information on labelling partitions - if you need it. It's about half way down. The author describes the use of mtools to label FAT partitions but I read somewhere else that it's not possible. Whatever - I use Windows to (re)label FAT partitions and e2label for ext3 ones.

This website ([http://www.debuntu.org/device-partition-labeling]("http://www.debuntu.org/device-partition-labeling")) gives some instructions on how to label partitions in various file systems, including a section on using mtools for vfat partitions. It looks like it's aimed at USB flash drives, but I guess it could be used for any partition on any device.

---

