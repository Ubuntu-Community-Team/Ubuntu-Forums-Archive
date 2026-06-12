---
title: "FAT32: can't delete file there"
date: 2005-08-03
forum: Desktop Environments
---

### Post by alquimista on 2005-08-03
Hi,
I have a FAT32 partition shared for WinXP and Kubuntu. Using Konqueror I can move and copy files but I can't delete them; I can do it just if I'm root in console. By the way, all directories in the FAT32 partition are in 777 mode.

Is there any config I'm missing? 

Thanx,
Guillermo

---

### Post by TravisNewman on 2005-08-03
add the option "umask=0000" to the fstab entry for your fat32

---

