---
title: "GRUB error; how to get around it and boot ?"
date: 2005-04-27
forum: Desktop Environments
---

### Post by davegahan on 2005-04-27
I get GRUB loading ERROR 17, and  cannot enter neither Ubuntu, neither windows. What can I do to get back into my system ?

---

### Post by defkewl on 2005-04-27
Did the grub console came out? Try entering the command by manually from those grub console

---

### Post by Fab on 2005-04-27
[QUOTE=davegahan]I get GRUB loading ERROR 17, and  cannot enter neither Ubuntu, neither windows. What can I do to get back into my system ?[/QUOTE]
 boot windows cd and enter rescue mode -> fixmbr at the cli -> reinstall grub
or
boot ubuntu install cd -> skip all stuff till grub installation -> reinstall grub

---

### Post by davegahan on 2005-04-27
I think when resizing my windows partition for a backup partition my MBR got overwritten or defective. I only get a text message GRUB loading.... ERROR 17. How to retrieve my files in my home directory ?

---

### Post by davegahan on 2005-04-27
I get back to the partition manager when I want to proceed with the GRUB reinstall... how do I proceed ? I cant afford any more mistakes. Configure Logical Volume Manager ? Could you provide a little more details ? Thanks !

---

### Post by Fab on 2005-04-27
[QUOTE=davegahan]I get back to the partition manager when I want to proceed with the GRUB reinstall... how do I proceed ? I cant afford any more mistakes. Configure Logical Volume Manager ? Could you provide a little more details ? Thanks ![/QUOTE]
 id suggest selecting manual edit, and then mount all the old partitions with the correct mount point (if you only had one linux partition, the mount point is /) 
be careful to not select format partition toh
im not 100% sure about this, so you should maybe wait for another reply ,)

---

### Post by davegahan on 2005-04-27
&#304;n that case will only GRUB be installed and not the system herbeby leaving my files intact ?

---

### Post by Fab on 2005-04-27
[QUOTE=davegahan]&#304;n that case will only GRUB be installed and not the system herbeby leaving my files intact ?[/QUOTE]
 it should

if you want to backup your data, put in any linux live cd and mount the old partitions to /mnt/something and burn that folder and subfolders on cd/dvd, a simple howto for mounting can be found at ubuntuguide.org

---

### Post by verzonen on 2005-04-27
I had the same problem, ubuntu fails to set/follow the boot flag properly

I fixed it by booting knoppix and with fdisk or cfdisk set the flag and reboot, ubuntu came up properly after that.

---

