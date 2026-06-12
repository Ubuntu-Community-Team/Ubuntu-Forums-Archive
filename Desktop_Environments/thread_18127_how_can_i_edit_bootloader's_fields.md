---
title: "how can i edit bootloader's fields?"
date: 2005-03-04
forum: Desktop Environments
---

### Post by lorap on 2005-03-04
friends, please help.
pavel

---

### Post by alastair on 2005-03-04
Please explain.

You mean the (grub) menu at boot (press ESC at startup)?

See the file :

/boot/grub/menu.lst

and edit via :

sudo gedit /boot/grub/menu.lst

BUT BE CAREFUL or you will make your system not bootable.

Check the docs.

---

### Post by lorap on 2005-03-04
yup, i needed to edit bootloader's menu.
there're some fields i don't ever use them like old kernel.
thanks friend.
pavel

---

