---
title: "How do you get rid of GRUB loader"
date: 2008-12-30
forum: General Help
---

### Post by dtrot55 on 2008-12-30
I had installed Ubuntu on one of my hard drives and I have since formatted that drive and use in windows...every time i restart now I get the GRUB loading... during the boot...how do i get rid of this?  I plan on using this drive for backup while I install Ubuntu on a different computer

---

### Post by exploder on 2008-12-30
Before you installed Windows you should have formatted the mbr, that is why you still have grub.

---

### Post by dtrot55 on 2008-12-30
so to format the mbr...would i just use partition magic or something to that effect to get rid of it?

---

### Post by SonnHalter on 2008-12-30
put in your windows install disc during bootup and boot from it. then go to recovery console and type "fixmbr"

---

### Post by ByKeLaO on 2008-12-30
You could also boot onto the Ubuntu LiveCD and run:
```
sudo lilo -M  /dev/Your-Disk-Here mbr
```
Obviously you need to replace Your-Disk-Here with the actual name of your disk.

---

