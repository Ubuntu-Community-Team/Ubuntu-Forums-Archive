---
title: "How to remove grub menue leaving just windows vista"
date: 2009-06-08
forum: General Help
---

### Post by rzscott0509 on 2009-06-08
I want to remove the grub menu. I have ubuntu 9.04 dual booted with windows vista. When I remove ubuntu and reboot im left with the grub menu giving me error 15 and not being able to boot windows. I dont have a windows vista cd by the way. So how to I get rid of the menu leaving just windows vista as the only OS?

---

### Post by 67GTA on 2009-06-08
You can use Super Grub Disk. It will fix the master boot record for Linux and Windows. Download the ISO, burn to CD, and boot as live CD.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Ocxic on 2009-06-08
just boot into recovery mode with you windows disk and run "fixmbr"

---

### Post by keplerspeed on 2009-06-08
Have a look here: [http://ubuntuforums.org/showthread.php?t=1146487](http://ubuntuforums.org/showthread.php?t=1146487)

Honestly I have never done it. But if you want to have vista as the only OS then you will need to fix the windows MBR.

Without the cd...use easyBCD [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) OR better still SUPERGRUB!

---

