---
title: "How do I make ubuntu first in the dual boot screen?"
date: 2009-02-05
forum: General Help
---

### Post by Shadow12313 on 2009-02-05
Hi, I have a dual boot between Ubuntu 8.10 and Windows Xp Home Edition and I want to know how I can make Ubuntu the first OS on the dual boot screen?

Any Ideas?

---

### Post by ieee488 on 2009-02-05
I don't know what happened with your install, but on my PCs, Ubuntu is always listed first and is the default OS to boot to.

---

### Post by GrooveTherapy on 2009-02-05
> **Shadow12313 said:**
> Hi, I have a dual boot between Ubuntu 8.10 and Windows Xp Home Edition and I want to know how I can make Ubuntu the first OS on the dual boot screen?

Any Ideas?
Are you using the grub bootloader?  if you are, 'grub' should appear a couple times before you get the option to select which OS to boot into.


If it is, you should be able to change the order in the /boot/menu.lst file.  I think this can be done by moving the lines with ubuntu 8.10 above the lines for your XP partition.

---

### Post by Shadow12313 on 2009-02-14
I am not really sure if I am using grub.  What should I do?

---

