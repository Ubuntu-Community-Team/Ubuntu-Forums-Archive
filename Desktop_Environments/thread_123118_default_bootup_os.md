---
title: "default bootup os"
date: 2006-01-29
forum: Desktop Environments
---

### Post by unionjak on 2006-01-29
hello,
because more than one person uses my pc, i would like the default os to be win xp, how do i do this ? 
many thanks.

---

### Post by lha on 2006-01-29
[QUOTE=unionjak]hello,
because more than one person uses my pc, i would like the default os to be win xp, how do i do this ? 
many thanks.[/QUOTE]

Boot Ubuntu and open terminal. Type
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
Find line
```
default 0
``` (The number might be different.) That number tells grub which menu entry to use as default. Numbering starts from 0. Change it to whatever you wish and save&exit. Boot and confirm you put the right number there.

---

