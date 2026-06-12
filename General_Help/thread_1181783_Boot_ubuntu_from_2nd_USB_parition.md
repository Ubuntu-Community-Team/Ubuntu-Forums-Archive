---
title: "Boot ubuntu from 2nd USB parition"
date: 2009-06-08
forum: General Help
---

### Post by Magnificence on 2009-06-08
Hi, I've managed well to create a USB Startup Disk on 1 partition of my stick, and leave another partition for storage.
Then when I run Windows I can't see the second partition. So I 'switched' the partitions. Now partition 1 is for storage and 2 for Ubuntu as USB Startup Disk.
Now I have another problem. Ofcourse partition 2 is flagged as boot, but it doesn't work now.
Does anyone know if it's possible to boot from a second partition? And how do you do that?

Else I put everything on 1 partition as solution.

---

### Post by C.S.Cameron on 2009-06-08
I you install from Live CD using the Ubiquity installer and manual partitioning, leaving a FAT32 partition for files should not be a problem, I normally make a third partition as ext3 for home and sometimes leave a little Linux swap.
If you are installing using usb-creator or Unetbootin I recall that if you partition the drive and make the first partition too small to install to, (<750MB), the second partition should end up automatically being the one installed to.
You can expand the first partition later using gparted.
If you stick with a single partition you will be able to find the files when booted from Ubuntu in filesystem / cdrom.

---

### Post by Magnificence on 2009-06-09
I have 2 partitions, 1st for storage and second with ubuntu on it. But my problem is that it wont boot from second partition and my question is if there is an other solution than put everything on the 1st partition.

---

### Post by Magnificence on 2009-06-11
Ok nevermind, it just seems that only my computer doesn't start up ubuntu from my second usb partition. All problems resolved now :P

---

