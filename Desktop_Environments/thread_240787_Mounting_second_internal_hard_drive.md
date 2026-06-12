---
title: "Mounting second internal hard drive"
date: 2006-08-21
forum: Desktop Environments
---

### Post by fedeecheverri on 2006-08-21
](*,) ](*,) ](*,)  I'm new to ubuntu. I have two internal hard drives, in one I have ubuntu installed, and the other one I just partitioned using gparted. I had to unmount it to be able to format it, but now I can not mount it. What can I do???  :-k

---

### Post by waldschm on 2006-08-21
use the command:

```
fdisk -l
```

to see what you have in terms of partitions and then go through and try mounting each of them using the mount command ie

```
sudo mkdir /media/internal
sudo mount -t ext3 /dev/hdb1 /media/internal
```

once you verify that they can be mounted properly, add them to your fstab file (/etc/fstab)

---

