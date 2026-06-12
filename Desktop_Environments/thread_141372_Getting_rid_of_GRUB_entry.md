---
title: "Getting rid of GRUB entry"
date: 2006-03-08
forum: Desktop Environments
---

### Post by ubuntukid on 2006-03-08
I had a copy of SUSE on my other hd when I installed ubuntu. Not anymore though as I reformated that hd but SUSE still shows in GRUB. How can I get rid of this?

---

### Post by kaamos on 2006-03-08
Try
```
sudo update-grub
```
and if that does not work, use
```
sudo nano /boot/grub/menu.lst
```
and remove the lines for the Suse entry.

---

