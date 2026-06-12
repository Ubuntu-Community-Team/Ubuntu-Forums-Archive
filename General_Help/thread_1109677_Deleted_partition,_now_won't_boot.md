---
title: "Deleted partition, now won't boot"
date: 2009-03-29
forum: General Help
---

### Post by LaGzo on 2009-03-29
I had 3 partitions. Vista, xp, and ubuntu. I deleted the xp to try and install windows7. It was at the beginning of the drive. When i try to boot now it says no operating systems detected. Can i fix it with ubuntu live cd? Thanks in advanced.

---

### Post by dcstar on 2009-03-29
> **LaGzo said:**
> I had 3 partitions. Vista, xp, and ubuntu. I deleted the xp to try and install windows7. It was at the beginning of the drive. When i try to boot now it says no operating systems detected. Can i fix it with ubuntu live cd? Thanks in advanced.

You need to reinstall Grub, do a forum search as there are HOWTOs on this.

---

### Post by LaGzo on 2009-03-29
Will it work if the boot manager I was using was the windows one? Since vista was installed last it used it's boot manager. I dont have ubuntu installed anymore either.

---

### Post by 4th guy on 2009-03-29
If you install windows, yes.

---

### Post by meierfra. on 2009-03-29
If you don't have Ubuntu you neither want nor will be able to reinstall Grub.  Your XP partition probably contained all the boot files for booting Vista. So you will have to the repair the Vista boot loader:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")

---

