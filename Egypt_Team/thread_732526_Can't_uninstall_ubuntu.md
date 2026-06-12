---
title: "Can't uninstall ubuntu"
date: 2008-03-23
forum: Egypt Team
---

### Post by angel_zone on 2008-03-23
i had recovered my NT boot loader successfully using super Grub and booted to windows i tried to use the partition magic to delete the linux partition but it keep telling me can't be deleted unsupported formate!! i  booted from the ubuntu live cd and started gparted it scans my hard drive so well but i couldn't delete exe part either ??it tells me can/t be deleted unmount any logical partition having a number higher than 8 ?? also there is a small lock sign besides the swap part that means that the partition is mounted?? how could that be as i'm working right now from the live cd?? any suggestions please

---

### Post by housam on 2008-03-23
You have to [[COLOR="Red"]_unmount the ext3 _[/COLOR]]("https://help.ubuntu.com/community/Mount#head-e2cd6350c74b57c36be49bc816c54f38a319e873")format partition to enable reformat or delete. 
Or just download [[COLOR="Red"]_the newer version of Gparted _[/COLOR]]("http://gparted-livecd.tuxfamily.org/")and burn it to a cd and boot from it as a live cd and use it to delete the ubuntu partition.

---

### Post by Moamen on 2008-04-04
which partition magic version do you use ?
have you tried any other partitioning app from windoz ?

---

### Post by ahmad_sayed on 2008-04-14
Try to use the Disk Manager in WindowsXP,
right click in My Computer -> manage
Select Storage and Disk Management

---

### Post by aiser on 2009-12-01
:ks

---

