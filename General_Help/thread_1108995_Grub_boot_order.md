---
title: "Grub boot order"
date: 2009-03-28
forum: General Help
---

### Post by UncleMonty on 2009-03-28
I want to shrink the windows partition on my parents PC and install ubuntu into a seperate partition using the ubuntu live cd. I've already done this on my old pc for practise but discovered ubuntu is now the default operating system. How can I change the boot order so that Windows XP is the default Operating System?

---

### Post by x33a on 2009-03-28
take a look here:

[http://ubuntuforums.org/showthread.php?t=75038](http://ubuntuforums.org/showthread.php?t=75038)

---

### Post by ibutho on 2009-03-28
You need to edit /boot/grub/menu.lst and change the line that starts with "default" to something like "default 1" or whatever number matches the entry for Windows. Remember that grub starts counting the entries from 0, so 1 is actually the second entry. Post back if you need more help with this.

---

