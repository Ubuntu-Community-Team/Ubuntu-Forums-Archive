---
title: "Trying to locate GRUB"
date: 2009-01-20
forum: General Help
---

### Post by goodtobegin on 2009-01-20
Hi, I know this can be a very ridiculous question, but I couldn't find an answer anywhere, so I post it here.

I installed Ubuntu and XP on my laptop, and had GRUB run so I could choose between the two. A week ago I decided to get rid of the Ubuntu partition, I ran Disk Management in Windows and formatted that partition to NTFS. As you might suspect, GRUB is still loading at boot.

I want to know how to get rid of GRUB. I read somewhere I need to fix the MBR, but I don't know how. I don't have an XP cd right now, I downloaded System Rescue CD and run GParted, but it only shows he partitions but no MBR.

I would appreciate any help. Thanks in advance.

---

### Post by rmills on 2009-01-20
Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console. Select your Windows XP installation from the list and enter the administrator password. At the input prompt, enter the command "FIXMBR" and confirm the query with "y". The MBR will be rewritten and GRUB will be uninstalled. Press "exit" to reboot the computer.

---

### Post by plucky on 2009-01-20
The OP does not have an XP CD but should be able to use the [Super Grub Disk](http://www.supergrubdisk.org/) to remove Grub from the MBR.Have never tried it so not sure.


Good Luck

---

