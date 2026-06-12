---
title: "boots to kernel"
date: 2007-11-07
forum: Desktop Environments
---

### Post by gtkourounis on 2007-11-07
i dunno what happened but i wanted to restart my computer, and next thing i know is ubuntu boots to the kernel. i start again, same thing happens, works just fine, it just fails to go through with the usesplash commands......

anyone know how to fix this????

---

### Post by neilengineer on 2007-11-08
In /boot/grub/menu.lst:

Add "ro quiet" after the kernel line.

---

### Post by gtkourounis on 2007-11-08
how exactly would i do that?

and thanx for the reply

---

