---
title: "My swap!"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Spug on 2005-04-14
Okay, this'll sound ridiculous, but I'm looking for my swap partition.

sudo fdisk -l
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7169     3613144+  83  Linux
/dev/hda2            7170       77117    35253792   83  Linux
/dev/hda3           77118       77622      254520   83  Linux
```

free
 ```
             total       used       free     shared    buffers     cached
Mem:        126972     124784       2188          0       3408      27816
-/+ buffers/cache:      93560      33412
Swap:       254512     127788     126724
```

So free seems to indicate I have a swap partition, but fdisk does not. I'm confused, but probably just ignorant.

---

### Post by Stormy Eyes on 2005-04-14
Look at /etc/fstab for a filesystem of type **sw**, and you'll have found your swap partition. It's probably /dev/hda3, by the way.

---

### Post by Spug on 2005-04-14
[QUOTE=Stormy Eyes]Look at /etc/fstab for a filesystem of type **sw**, and you'll have found your swap partition. It's probably /dev/hda3, by the way.[/QUOTE]
 It is. /dev/hda3 shows up with ID 83 in fdisk, though :/ So I ran the following:

$ sudo mkswap /dev/hda3
$ sudo swapon /dev/hda3
swapon: /dev/hda3: Device or resource busy

It's busy. Does that mean it's already being swapped to, but is shown as an 83 partition in fdisk still for some reason?

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=Spug]It's busy. Does that mean it's already being swapped to, but is shown as an 83 partition in fdisk still for some reason?[/QUOTE]

Chances are the Ubuntu installer created it as type 83 when partitioning your HD. If you really wanted to, you could probably boot using the Ubuntu LiveCD, alter the partition's type to 82, run mkswap /dev/hda3, and then reboot, but why screw with it if it works?

---

