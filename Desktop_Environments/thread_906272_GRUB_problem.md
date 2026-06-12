---
title: "GRUB problem"
date: 2008-08-31
forum: Desktop Environments
---

### Post by Aspras on 2008-08-31
Hello, i have been trying to uninstall Ubuntu for a while but it seems like GRUB is bringing me trouble. When i try to boot from a Windows CD in order to get to the repair command prompt GRUB loads up before my pc boots from the CD so i cant get there.

---

### Post by kellemes on 2008-08-31
> **Aspras said:**
> Hello, i have been trying to uninstall Ubuntu for a while but it seems like GRUB is bringing me trouble. When i try to boot from a Windows CD in order to get to the repair command prompt GRUB loads up before my pc boots from the CD so i cant get there.

Enter your BIOS and set the diskdrive first in the bootorder, otherwise it will try to boot your harddrive first and bypass the bootdisk.

---

### Post by ubunix on 2008-08-31
it should be F2 or F12

---

### Post by sandysandy on 2008-08-31
try pressing [COLOR="Red"]*delete*[/COLOR] key after rebooting ur computer.

that should give u BIOS menu.

change booting priority to CD ROM then hard drive

regards

---

### Post by Aspras on 2008-08-31
I have already done that, my bios is set to boot from the drive i have my windows cd in but GRUB keeps blocking it somehow.

EDIT: Never mind, it looks like my Windows CD is the problem because i was able to boot with my PARAGON Safe Disk. Problem solved thanks for the support.

---

