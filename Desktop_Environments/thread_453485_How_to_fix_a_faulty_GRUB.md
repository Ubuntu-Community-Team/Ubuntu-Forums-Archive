---
title: "How to fix a faulty GRUB?"
date: 2007-05-24
forum: Desktop Environments
---

### Post by kpfuser on 2007-05-24
To give Ubuntu a try, I installed Feisty Fawn in a pc with 5 hard disks (4 IDEs and 1 SATA). At its initial state the pc had Windows 2000 installed in the first hard disk (IDE-0). Just before installation, I placed IDE-1 at the top of the booting list hoping (erroneously as it turned out) that Ubuntu would confine itself on this disk alone and leave the other hard disks intact.

The installation went smoothly. However, when I rebooted, the grub prompt that appeared would not revert to the list of bootable OSs by hitting ESC. Fortunately, more by luck than anything else, I found a workaround (striking TAB and then ESC twice in quick succession) to get to the list of bootable OSs. Nevertheless, I could not get the default OS (Ubuntu) to boot automatically after the standard 10 sec (or longer) delay.

Since my workaround allows me to boot into Ubuntu, I am able to view and edit the menu.lst file. The problem is that I have been unable to find concrete info regarding what specific editorial changes are needed to make grub work as intended, i.e. revert to the booting table when hitting ESC and then boot Ubuntu automatically 10 sec later.

Any ideas as to how to fix grub?

---

### Post by orb9220 on 2007-05-24
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)
[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

Hope one of these can help you.

---

