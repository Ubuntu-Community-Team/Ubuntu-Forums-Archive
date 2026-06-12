---
title: "Boot order"
date: 2006-08-04
forum: Desktop Environments
---

### Post by lugos on 2006-08-04
Hello,

I just installed Ubuntu 6.06 on my Windows XP laptop.  Is it possible to make Windows the default OS to boot instead of Ubuntu?

Any help would be greatly appreciated.

Thanks,
lugos

---

### Post by cantormath on 2006-08-04
> **lugos said:**
> Hello,

I just installed Ubuntu 6.06 on my Windows XP laptop.  Is it possible to make Windows the default OS to boot instead of Ubuntu?

Any help would be greatly appreciated.

Thanks,
lugos

you need to change that in grub.
sudo gedit /boot/grub/menu.lst
To change the order, all you do is copy and paste them to be in the order you want.

or

open /boot/grub/menu.lst file (type "sudo gedit /boot/grub/menu.lst" in terminal) and find the following option:

default number 

where "number" should be 0 to boot the first entry in the menu, 1 for the second and so on.

---

### Post by lugos on 2006-08-04
Nevermind, I found my answer.

---

### Post by scxtt on 2006-08-04
or edit the line that says **default #** where # is the one you want to be default (remember that it starts w/ 0)

---

### Post by lugos on 2006-08-04
Thank you cantormath, your first option is the one I found and it worked.

---

