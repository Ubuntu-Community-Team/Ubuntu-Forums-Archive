---
title: "problem dual booting ubuntu and xp"
date: 2009-05-28
forum: General Help
---

### Post by amal hashim on 2009-05-28
i had *Ubuntu* 8.10 "[I]Intrepid installed in one of my hard disk partitions with no other operating systems along with it.
now i installed windows xp in another partition and upon restart windows is working fine but i dont get to choose the operating systemand so i cant get into the installed ubuntu..........

the installation files and the partitions still exists when i checked using live cd of ubuntu, but i seem to have somehow lost the boot up choice of ubuntu....
 
can anyone help me with this...i need to solve this fast as i need that hard disk space and i cant even format it or reinstall in that partition........
[/I]

---

### Post by Altay_H on 2009-05-28
It sounds like you accidentally overwrote GRUB with MBR. You can revert to using GRUB (the bootloader that allows you to choose which operating system to boot) by following this guide over here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

