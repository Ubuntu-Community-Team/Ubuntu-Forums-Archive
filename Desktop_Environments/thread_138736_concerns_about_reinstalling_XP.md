---
title: "concerns about reinstalling XP"
date: 2006-03-02
forum: Desktop Environments
---

### Post by Cirrocco on 2006-03-02
I currently have XP on partition 1 and ubuntu on partition 2.
XP was installed first, and ubuntu second

I want to reinstall XP on partition 1 and leave ubuntu alone

if during the reinstall I delete partition 1 (leave 2 alone) and reformat will this break GRUB?

what's the best way to get this done?

---

### Post by Ramses de Norre on 2006-03-02
Deleting wont affect grub (just don't choose the line for the ex-xp partition), but reinstalling will!
There are a lot of threads on the forum about reinstalling grub ( use search function ).

---

### Post by skirkpatrick on 2006-03-02
Deleting partition 1 and reformating won't hurt Grub as it won't touch the MBR.  However, when you reinstall XP, that will overwrite the MBR and break Grub.  My suggestion is to burn a copy of the Live CD and use it to reinstall Grub after you reinstall XP.  There's a topic about that here in the forums somewhere if you search for it.

My favorite way to dual-boot now is something else I found in the forums.  It requires two drives, though.  You put the Windows drive as the master and only drive in the system, and do an install or use **fdisk /mbr** to make it boot to Windows.  Then you move it to either the secondary channel or the slave drive and put your Ubuntu drive in the primary master position.  Install Ubuntu or reinstall Grub so that Grub sits in the primary master MBR.  Then you use the map command in your menu.lst file so that when you boot Windows, it thinks it's the primary master drive and any changes to it will only affect the MBR on the Windows drive.  With this setup, you can pull the Windows drive out without affecting Ubuntu and even put it in another system as the primary master without affecting Windows.

---

