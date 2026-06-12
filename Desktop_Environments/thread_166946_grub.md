---
title: "grub?"
date: 2006-04-27
forum: Desktop Environments
---

### Post by azray on 2006-04-27
How do I change the boot sequence? I want to change the default dual boot.

---

### Post by Ramses de Norre on 2006-04-27
sudo gedit /boot/grub/menu.lst
Search the line starting with Default and change the number to the kernel you want to be the default, start counting from zero with the first listed kernel.

---

