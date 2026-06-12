---
title: "Does deleting partition change designation of other partitions?"
date: 2009-04-21
forum: General Help
---

### Post by michy99 on 2009-04-21
Here is a screenshot of my current configuration. I want to delete sda2 and let sda1 use the space. When I delete sda2, does sda3 then become sda2 and sda4 become sda3 etc., or will there just not be an sda2 and everything else remain the same? If it does change, will I have to edit my fstab and grub menu to reflect the changes?

---

### Post by StuartN on 2009-04-21
The parted manual [http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html](http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html) implies that all higher numbers do change when you remove a partition.

---

### Post by michy99 on 2009-04-21
Ok, I removed sda2 and expanded sda1. The other partitions remained the same. There is no longer an sda2. Rebooted and everything works fine. Apparently the comment about the numbers changing for the higher partitions applies only to Windows. Since my Windows partition is the first one I guess there is nothing to change.

---

### Post by Cheesemill on 2009-04-21
The partition number on a drive can change, even without adding/removing partitions. Check out this for a brief explanation:

[http://ubuntuforums.org/showthread.php?t=638076]("http://ubuntuforums.org/showthread.php?t=638076")

---

