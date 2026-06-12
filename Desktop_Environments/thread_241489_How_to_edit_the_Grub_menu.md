---
title: "How to edit the Grub menu?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Chrono86 on 2006-08-22
Hey guys~
I accidently installed the older kernel (version 25) and now the Grub menu shows both the current version (26) and 25. I removed the older kernel from the package manager but it still shows up in Grub...how do I remove it from there?
Thanks
Adam

Oh, and by the way, is there a way to make Grub look nicer?

---

### Post by Ramses de Norre on 2006-08-22
Are you sure you removed the older kernel correctly? That should remove it form the grub menu..
Try ```
sudo update-grub
``` to regenerate the grub menu, if it's still there you'd check synaptics/dpkg -l for linux-image-version.

To be complete: the grub menu is configured throug /boot/grub/menu.lst, which you can edit if you want, but be carefull and read the comments.

---

### Post by kwalo on 2006-08-22
You can also edit the **/boot/grub/menu.lst** by hand. Use [code]sudo your_favourite_editor /boot/grub/menu.lst[/b]. Read the comments carefully. Sure you can make it.

---

### Post by Ramses de Norre on 2006-08-22
Yes but if you just delete the lines for an installed kernel, they will reappear on every kernel upgrade/removal..

---

### Post by kwalo on 2006-08-22
> **Ramses de Norre said:**
> Yes but if you just delete the lines for an installed kernel, they will reappear on every kernel upgrade/removal..

Maybe you haven't removed the old kernel version. Use synaptic, or type in:
```
sudo apt-get remove linux-image-2.6.15-25* linux-restricted-modules-2.6.15-25*
```If you want to remove 2.6.15-25 kernel. Then just delete lines corresponding to that kernel in /boot/grub/menu.lst

---

