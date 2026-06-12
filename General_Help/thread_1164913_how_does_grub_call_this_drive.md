---
title: "how does grub call this drive?"
date: 2009-05-20
forum: General Help
---

### Post by chriskin on 2009-05-20
if the first partition is an extended one, and i want to use the second partition of that extended one, what would grub call that?
(hd0,0,1) ?  or (hd0,something else?) 

cause it surely doesn't go at (hd0,1) because my second partition (the one after the extended) surely has that name on grub

---

### Post by dandnsmith on 2009-05-20
The number are roughly aligned with those got from *fdisk* - so if you have a standard setup, there may be gaps in the numbers (sda1, sda4, sda5, sda6) but grub usage would be similar, but starting from zero (hd0,0) (hd0,3) (hd0,4) (hd0,5).
The logical partitions (drives in Windows parlance) don't look any different from primary, and neither does an extended partition to grub - it's just a question of what they are used for.

HTH

---

### Post by chriskin on 2009-05-20
> **dandnsmith said:**
> The number are roughly aligned with those got from *fdisk* - so if you have a standard setup, there may be gaps in the numbers (sda1, sda4, sda5, sda6) but grub usage would be similar, but starting from zero (hd0,0) (hd0,3) (hd0,4) (hd0,5).
The logical partitions (drives in Windows parlance) don't look any different from primary, and neither does an extended partition to grub - it's just a question of what they are used for.

HTH

i'll try what you said  then
thanks :)

---

