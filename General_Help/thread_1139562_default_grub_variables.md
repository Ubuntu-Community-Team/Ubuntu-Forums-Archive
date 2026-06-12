---
title: "default grub variables?"
date: 2009-04-27
forum: General Help
---

### Post by Bultot on 2009-04-27
I've used WUBI before. After that I've converted the installation to real partitions.
Now every time I install a new kernel, the grub menu updates itself with the WUBI variables. Then I have to manually adjust the kernel line for booting.
I'm looking for a way to change the default vars of the grub menu.

---

### Post by mcduck on 2009-04-27
All the defaults are in the very same file, /boot/grub/menu.lst. Just read through the file and you should easily find the default settings section and explanations for every setting.

---

