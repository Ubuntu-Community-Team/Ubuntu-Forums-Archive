---
title: "AGGGHHHH usb flash drive"
date: 2009-03-25
forum: General Help
---

### Post by Hellstudios on 2009-03-25
this is the error I get after trying to format my thumb drive to the FAT file system to run DSL.....


"cannot mount volume - the volume 'LAWL DRIVE' used the FAT file system, which is not supported by your system"



any ideas? D: :(


I hope I didn't Permanently cause it to not work in Ubuntu. D:

---

### Post by Hellstudios on 2009-03-25
Bump.

---

### Post by Hellstudios on 2009-03-25
BTW, I put it in a winblows machine, Tried to format it, said it was completed successfully, also says it is now FAT32, I put it in my Linux machine, and still nothing. says it's still fat32.....




God I hate computers.

---

### Post by kanikilu on 2009-03-25
Can you see it in gparted? Or ```
sudo fdisk -l
``` If it's not mounting, maybe ```
dmesg | tail
``` might have an error or something to point you in the right direction.

---

### Post by Hellstudios on 2009-03-25
Yeeeaahh.... I don't know how to use gparted. D:

---

