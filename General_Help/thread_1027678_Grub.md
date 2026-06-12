---
title: "Grub"
date: 2009-01-01
forum: General Help
---

### Post by RedSingularity on 2009-01-01
How can i remove boot loaders from grub?  Say i want to remove the windows boot option from grub how can i do it?  Thanks.

---

### Post by utter-imadness on 2009-01-01
You can edit your menu.lst file in your /boot/ folder and remove the windows option. Or you can install a program to do it for you such as "kgrubeditor" from the package manager.

---

### Post by caljohnsmith on 2009-01-01
If you first open a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
Then if you look for the Windows entry (usually near the bottom of that file), you can delete it. The entry will probably look similar to:
```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
```
Let me know how that goes or if you run into problems. :)

---

### Post by RedSingularity on 2009-01-01
Ahhhh worked like a charm!  Thanks for the input guys.  Appreciate it!

---

