---
title: "grub error 24"
date: 2006-09-24
forum: Desktop Environments
---

### Post by secret_force on 2006-09-24
Hi,
 
I tried to re-partion my harddisk but I guess it went wrong. Now when I boot my computer I get error message 24 in grub 1.5.
Does anyone know what to do :confused:
I used cfdisk to repartion my harddisk and use kubuntu 6.06

---

### Post by lagagnon on 2006-09-24
Use the Ubuntu Live CD, choose Ubuntu Repair, and post the output of the following commands to this thread:

fdisk -l
df

You also should mount the partition on which you installed Ubuntu (eg: mkdir /mnt/test ; mount /dev/??? /mnt/test) and then post the output of this command to this post:

cat /mnt/test/boot/grub/menu.1st

---

### Post by secret_force on 2006-09-24
> 
Use the Ubuntu Live CD, choose Ubuntu Repair


what do you mean with "ubuntu repair"? There is no such option on the life cd. Do you mean "start or install ubuntu"

---

### Post by blip on 2006-09-24
Looks like your MBR is messed up.  Pretty simple fix assuming that there isn't further damage somewhere.

Here are your options:
A) As already noted use the repair disc.
B) Start an ubuntu installation but only perform the GRUB install step.
C) Reinstall groub manually.

Personally I like C. Boot up with a live disc (ubuntu, knoppix, whatever) and reinstall grub from there.  There are three or four methods for doing this... I think last time I had to repair an MBR I used the second method in this thread: [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

---

