---
title: "Removing Ubuntu"
date: 2007-06-16
forum: Desktop Environments
---

### Post by bryan_M23 on 2007-06-16
alright, here's my problem. i was testing out Ubuntu on my parents computer, i had a separate ATA drive which Ubuntu was installed on. i now got my own computer, so i installed Ubuntu on that. now, my parents want Ubuntu removed from the system. fair enough, i was the only one using it but now i dont use that computer now that i have my own. so i figgered just remove the Ubuntu Drive, i wanted to put it for extra space in my computer anyway. but when i rememoved it, i booted the system and instead of launching windows like it used to, it said there was an error in the grub loader. how can i fix this, so that just windows loads and my parents dont kill me.

---

### Post by ugm6hr on 2007-06-16
You need to reinstall the Windows bootloader (which Ubuntu over-wrote).

General principle (for XP):
Boot from Windows CD, go to Recovery mode (I think you type "R"), type the *fixmbr* command.

Just do a quick search for fixmbr on this forum to make sure that's correct.

---

