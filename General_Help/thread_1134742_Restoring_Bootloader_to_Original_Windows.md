---
title: "Restoring Bootloader to Original Windows"
date: 2009-04-23
forum: General Help
---

### Post by strikewolf42 on 2009-04-23
Hey everyone~

I have several questions.

1: If I remove GRUB, can I still boot Ubuntu?

2: If I cannot remove GRUB and still boot Ubuntu, is there a way I can make it so it automatically highlights my Windows XP installation and boots that up automatically? (i.e. I turn my computer on in the morning and get coffee, I want it to automatically boot XP, not Ubuntu).

3: If I cannot do number 1 or 2, would it be safe to format the drive I installed Ubuntu on, and will everything be back to normal?

Thanks for your time, all replies welcome.

---

### Post by Titan8990 on 2009-04-23
1) not unless you install lilo

2) Change the lines in /boot/grub/menu.lst so that Windows is the first option. Do this by copy and pasting it above the Ubuntu entries. This will be 3-4 lines, each entry will be separated by an empty line. In case of problems, back up menu.lst with the following: sudo cp /boot/grub/menu.list /boot/grub/menu.list.bak

3) no, you have to reinstall the windows bootloader.

---

### Post by strikewolf42 on 2009-04-23
> **Titan8990 said:**
> 1) not unless you install lilo

2) Change the lines in /boot/grub/menu.lst so that Windows is the first option. Do this by copy and pasting it above the Ubuntu entries. This will be 3-4 lines, each entry will be separated by an empty line. In case of problems, back up menu.lst with the following: sudo cp /boot/grub/menu.list /boot/grub/menu.list.bak

3) no, you have to reinstall the windows bootloader.
Alright thanks, I'll try these and report back on how things go.

---

