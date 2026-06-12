---
title: "Question about the grub loader"
date: 2005-08-06
forum: Desktop Environments
---

### Post by glowstick on 2005-08-06
Right now the default boot is to Kubuntu, but how do I set it so it boots to Windows XP by default instead?

---

### Post by xhaker on 2005-08-06
edit /boot/grub/menu.lst
you need to change the line that says -> default 0
to -> default 4 
depending on the number of options

---

### Post by glowstick on 2005-08-06
Thanks for the quick reply

---

