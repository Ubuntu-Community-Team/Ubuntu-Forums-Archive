---
title: "[SOLVED] Recovering lost files (Important Pictures)"
date: 2009-06-09
forum: General Help
---

### Post by drew212 on 2009-06-09
I recently upgraded from jaunty to jaunty x64, and I lost all my files, including some pictures that were pretty important. Is there any way to scan my hard drive for the pictures possibly? Is there a program I can use to pull them off the SD card I put them on, I haven't used the card since i moved the pictures off the card.

---

### Post by aysiu on 2009-06-09
Yes, you can do it with *photorec*, which is part of the *testdisk* package.

More details here (instructions are for Windows, but it's pretty easy to see how you would tweak them for Ubuntu):
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by drew212 on 2009-06-09
Ok, but now how do i change the owner from root to my home file? I cant do anything with the files, and when i copy them to a new file i get a new error, im at work right now so i dont have the exact error message on hand.

---

### Post by aysiu on 2009-06-09
> **drew212 said:**
> Ok, but now how do i change the owner from root to my home file? I cant do anything with the files, and when i copy them to a new file i get a new error, im at work right now so i dont have the exact error message on hand.
Let's say they're in /media/disk/recovery and your username is drew: ```
sudo chown -R drew:drew /media/disk/recovery
```

---

### Post by drew212 on 2009-06-10
Thanks so much, problem solved =).

---

