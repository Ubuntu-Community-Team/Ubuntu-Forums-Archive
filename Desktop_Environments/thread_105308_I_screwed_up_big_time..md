---
title: "I screwed up big time."
date: 2005-12-18
forum: Desktop Environments
---

### Post by saldie on 2005-12-18
Hi, I really need some help here please.
I put an extra hard drive in my comp. formated it and installed mepis, just to try it.
Like an idiot i over-wrote my menu.lst, and now i cant get into ubuntu.
I can open the menu.lst file in mepis but i am unsure what to input. I tryed a few different lines from reading some of the posts here but its not working.
Can someone please help me out.

---

### Post by kosmic on 2005-12-18
In what drive did you have Ubuntu installed ?
 
do as root or with sudo the following comand in a terminal :
 
fdisk -l (it's a small L)

---

### Post by DiscoKiller on 2005-12-18
if u can get to the terminal screen in mepis try this howto for restoring grub
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by saldie on 2005-12-18
Kosmic, here it is:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2611    20972826   83  Linux
/dev/hda2            2612        2807     1574370   82  Linux swap / Solaris
/dev/hda3            2808        9729    55600965   83  Linux

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2611    20972826   83  Linux
/dev/hdb2            2612        2741     1044225   83  Linux
/dev/hdb3            2742        9964    58018747+  83  Linux

Ubuntu is on hda.

Discokiller, i cant boot into the install or live cd for some reason.

---

### Post by saldie on 2005-12-18
Never mind got it.

---

