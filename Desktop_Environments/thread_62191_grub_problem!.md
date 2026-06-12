---
title: "grub problem!"
date: 2005-09-03
forum: Desktop Environments
---

### Post by tmasboa on 2005-09-03
I installed grub and did what it said in the Ubuntu guide to add winblows, but Windows won't boot! it says something about a unknow filesystem. Will it not boot Windows because it is NTFS?

HElp!
Thanks  :)

---

### Post by essexman on 2005-09-03
[QUOTE=tmasboa]I installed grub and did what it said in the Ubuntu guide to add winblows, but Windows won't boot! it says something about a unknow filesystem. Will it not boot Windows because it is NTFS?

HElp!
Thanks  :)[/QUOTE]
Grub doesn't need to know the filesystem, only where it is.  For windows it will boot into the windows bootloader.  Windows must be on the first partition of the first drive.  In grub this is (hd0,0) and in Linux this is /dev/hda1.

Can you post your menu.list file and the full error message? I'm sure someone will spot something.

---

