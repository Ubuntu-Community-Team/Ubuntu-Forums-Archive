---
title: "Endless lines of the word GRUB when trying to boot"
date: 2008-12-14
forum: General Help
---

### Post by T.lancer on 2008-12-14
hey, my home sever is on the fritz again.  when it starts to boot it will instantly start displaying endless lines of the word GRUB, with no other messages before or after.

tried to reinstall grub, no luck.  anyone got any ideas?

---

### Post by Bob John on 2008-12-14
use dos\win98 floppy disk to start machine , type command : "format /mbr" at prompt .
then download grub4dos and set it up. Good luck !

---

### Post by hikaricore on 2008-12-14
If memory serves, using the above method you run the risk of data loss if something goes wrong...

Proceed with caution.

---

### Post by T.lancer on 2008-12-14
I know of the win 98: fdisk /mbr command, I'll try that first, as I know that doesn't cause dataloss.

---

### Post by geirha on 2008-12-14
Gentoo's [GRUB Error Collection](http://www.gentoo.org/doc/en/grub-error-guide.xml) says this about the problem:
> According to airhead this can be caused by having your bios detect your disks automatically. Try to set your bios entry to User Type HDD.

Another possibility is that you had Grub installed on your MBR and tried reinstalling it (for instance due to hard disk changes) but used the wrong setup and root commands. 

Worth a try to see if that bios setting will fix things.

---

### Post by T.lancer on 2008-12-14
I fixed it, seemed my bios was trying to boot from the wrong drive, which may have still had some left over Grub stuff on it.  set it to the right drive, and it's booting now.  No idea why it would do this now.  I havn't changed anything hardware related in ages... strange.

---

