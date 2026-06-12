---
title: "10 GB to 20 GB"
date: 2009-01-15
forum: General Help
---

### Post by tigga on 2009-01-15
Hi. I have ubuntu partition which is taken 10GB and i want to upgrade it to 20GB without losing my data or formating the partition.
Anyone can help me ??

---

### Post by djbushido on 2009-01-15
do this:
make an iso of the live cd [here]("http://gparted.sourceforge.net/").

You can then use the livecd to resize the disk.

You also have to change the uuid in grub to reflect the change, so

```
ls /dev/disk/by-uuid -lha
``` will tell you the uuid's of all the partitions in the root filesystem. then change /boot/grub/grub.conf to reflect this. 
Now you're good to go!

---

### Post by redilyn on 2009-01-15
If you just resize the partitions you won't have to worry about the UUID, they don't change during a resize.

Just boot from the livecd and resize with the partition editor then reboot.

Good to go.

Cheers

---

