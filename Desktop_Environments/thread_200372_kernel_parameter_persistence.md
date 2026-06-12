---
title: "kernel parameter persistence"
date: 2006-06-20
forum: Desktop Environments
---

### Post by chenlevy on 2006-06-20
Hello,

On my AMD Athlon XP I found I need to add as kernel parameters "noapic" and "pci=biosirq", for my machine to function properly.

But when I put these parameters in menu.lst they get lost every time there is a kernel update via apt-get.

My question is where should I configure the extra kernel parameters, so it will be appended to the entries in menu.lst automatically with a kernel updates?

TIA,
Cheers,
Chen.

---

### Post by Ramses de Norre on 2006-06-20
Find the line in /boot/grub/menu.lst starting with ```
# defoptions=
``` and add the options to the end, don't mind the comment, that's normal. 
Then run sudo update-grub to apply all defoptions to your kernels, this command is also automaticaly run on every kernel update so all new installed kernels have this options.

---

### Post by chenlevy on 2006-06-20
Very cool.
Thanks.

Cheers,
Chen.

---

