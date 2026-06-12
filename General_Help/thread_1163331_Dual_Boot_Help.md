---
title: "Dual Boot Help"
date: 2009-05-18
forum: General Help
---

### Post by hothail on 2009-05-18
Ok, here is my scenario.

I have been running Ubuntu for a couple months and the other day i just installed Windows XP.

Ubuntu all of a sudden didn't work, so i just reinstalled grub by doing

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```

Now i can't boot back into windows.  Should i just fix the mbr using the windows xp disk? And if i do how can i get it so i can actually dual boot with both working?

EDIT: I forgot to say that ubuntu and windows are on different partitions on the same hard drive.

---

### Post by hothail on 2009-05-18
bump

---

### Post by hothail on 2009-05-18
bump

---

### Post by hothail on 2009-05-18
bump

---

