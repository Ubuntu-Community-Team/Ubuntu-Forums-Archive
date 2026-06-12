---
title: "ubuntu/xp db setup, ubuntu will not bootup!"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by manij on 2007-09-01
I have dimension 3100 160G SATA HD.

I wiped out the recovery partition and the intial dell utility partition and manually configured the partition such that I left the XP installation alone and installed dapper. The installation is successful however, upon reboot, I do not the choice of operating systems and it directly boots to XP.

Is this a GRUB problem? 

I did the same thing on my t'pad R51 with any problem and am posting from it using ubuntu!

Help!

---

### Post by seshomaru samma on 2007-09-01
I suspect you installed Grub to the wrong place.
You should have installed it to the MBR (hd0)
another possibility is that your computer has some sort of MBR protection but I think that's unlikely.
Just reinstall Grub and you should be OK
[(howto]("http://ubuntuforums.org/showthread.php?t=224351"))

---

