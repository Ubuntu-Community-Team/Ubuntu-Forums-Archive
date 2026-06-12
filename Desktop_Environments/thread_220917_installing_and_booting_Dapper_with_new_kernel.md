---
title: "installing and booting Dapper with new kernel"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Tibor60 on 2006-07-22
I have found an interesting problem when switching to Dapper Drake, and to find the solution was not so easy. Maybe it is useful to tell my experiment for other people...
I have a PCI IDE card installed, with a hard drive on it. And Dapper Drake from the installing CD start count from the built in IDE card, so the first PCI IDE Master channel is the hde1. The first built in IDE Master channel is hda1. The installer built the GRUB menu.lst (root=/dev/hda1...) The same wuth the /etc/fstab file...
That is nice, but the system can not boot, as Dapper Drake start the count from the PCI IDE card, and can not mount the root file system, because the first built in IDE Master channei is already on hde1. So when installing Drake, I could only install with the alternate (consol) installer, when the installing process is ready, I receive a non-booting system. Here on hand a rescueCD, I boot with the rescue CD, edit the /etc/fstab and the /boot/grub/menu.lst files, and after this changes the system is booting normally, funtioning without problem.
BUT ONLY UNTIL THE NEXT KERNEL UPDATE! Then the update process messes up again the menu.lst and fstab. So after every kernel update there is a need to edit these files form a rescue CD...

BTW, I hope that this bug should be corrected soon...

---

