---
title: "Boot Loader Issues"
date: 2009-05-12
forum: General Help
---

### Post by lechatfou on 2009-05-12
Please help me with this, as I am a total Grub n00b.
I have two drives, a 250 GB SATA and a 10 GB IDE.  The SATA drive, hd1, has three partitions: 
Partition 1: Win XP
Partition 2: HP Recovery
Partition 3: Win 7

The IDE drive, hd0, is installed with Ubuntu.  I have just installed Windows 7 in the past few days.  Before I installed it, I had the bios set to boot hd0 first, present me with the Grub menu, and I would choose between Ubuntu and XP.  When Windows 7 was installed, it overwrote the MBR of hd1 with the Windows 7 boot manager, but since Grub was installed on the other drive, it was preserved. So, therefore, the Grub menu option that would have previously let me boot XP straightaway, boots hd1 and I am presented with the less-than-appealing Windows boot menu which lets me choose between XP and 7. ](*,)  I do not like going through two separate boot menus just to boot XP or 7.  So my question is: Can I add 7 to Grub? and how? Or can I add Ubuntu to the Windows boot menu?  (I think I have made it clear, however, that I would prefer the former.) 
Thanks in advance for your help, :) and please tell me if I am not making things clear enough.

---

