---
title: "HELP! Need to delete the GRUB!"
date: 2006-05-11
forum: Desktop Environments
---

### Post by jrs1985 on 2006-05-11
I deleted my partitions of ubuntu using partition magic (I dual-booted ubuntu & xp)  However, when I reset my computer, the GRUB boot loader says error 22 and I can't laod anything. I tried putting in the windows xp cd to boot, but this didn't help. I could run the ubuntu install cd, but it won't let me install the grub loader without first repartioning the drive. When i try to resize my windows NTFS  , its says operation failed resizing. 

Is there a way to erase the GRUB boot loader so windows will boot normally?


THANK YOU!

---

### Post by Ramses de Norre on 2006-05-11
Insert a windows install cd and choose resque prompt (or something with a similar name). Then type fixmbr and quit (or exit) to reboot. Your windows-only mbr should be made then.

---

### Post by linuxcity on 2006-05-11
I do not know about the command "fixmbr"
but  "fdisk /mbr"  worked for me.

---

