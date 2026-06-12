---
title: "How to reisntall GURB in Ubuntu DD"
date: 2006-08-03
forum: Desktop Environments
---

### Post by true_friend on 2006-08-03
Hi i am using Ubuntu 6.06. Gurb gave error 17 and i had to fix my mbr from Recoery console of Xp.tell me how can i install it again.
Regards
True_Friend

---

### Post by ravindran.k on 2006-08-03
Hi true frnd,
 
Do you have a Ubuntu CD? Please boot using that in Resecue mode...
Then, please dump all your partiton tables details..you can do that using fdisk command:
 
# fdisk /dev/hda
and then p
..Do this for all /dev/hd[b,c,d]...
 
Then we can advise u better..

---

### Post by Ramses de Norre on 2006-08-03
Boot into the live cd, open up a terminal and do
```

sudo grub
root (hd0,0)
setup (hd0)
quit

```
With: 

*(hd0,0) the device and partition containing /boot/ (first number of hard disk, then number of partition. Start counting from zero, hd0,0=hda1)

*(hd0) the device and partition to install grub to, hd0=MBR.

---

### Post by true_friend on 2006-08-03
> **Ramses de Norre said:**
> Boot into the live cd, open up a terminal and do
```

sudo grub
root (hd0,0)
setup (hd0)
quit

```
With: 

*(hd0,0) the device and partition containing /boot/ (first number of hard disk, then number of partition. Start counting from zero, hd0,0=hda1)

*(hd0) the device and partition to install grub to, hd0=MBR.
could not install grub using the method . it could not find the file at /boot/grub/stag1.
tried to boot in rescue mode but could not find this option in Ubuntu 6.06 live/install cd.
some one guide me to boot in rescue mode??
i found two very simple commands to restore boot loader
they are::
```

chroot /mnt/sysimage
grub-install /dev/hda

```
i will be very thankful for this kindness.
Regards
True_Friend

---

### Post by gargoyle on 2006-08-09
Per your suggestion I typed in 
**locate mgetty**

There was not responce.
Did not seem to find it does that mean it was not actually installed?

---

