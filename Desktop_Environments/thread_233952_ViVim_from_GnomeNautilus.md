---
title: "Vi/Vim from Gnome/Nautilus?"
date: 2006-08-10
forum: Desktop Environments
---

### Post by burke2134 on 2006-08-10
Greetings,

Is there anyway to open a file (e.g. a *.txt file) with Vi or Vim by *double-clicking* on the file in a Nautilus window?

Thanks in advance for your knowledge...

-burke

---

### Post by mssever on 2006-08-10
Ahh, a fellow vi user...

My approach is to use the terminal for everything :)

If you right-click on a file in Nautilus there will probably be an Open with submenu. On my system, Gvim is one of the options (of course, you have to install it with synaptic or similar). Also you can try using the Open with other application menu item (in the same place) and enter something like ```
gnome-terminal -e vi "%s"
```. I haven't tested it, so you might need to play with it a bit.

---

### Post by gThree on 2006-08-10
In Gnome I think you can right-click a text file (in your example) and select Properties >> Open With and then check the application you want to set as the default.

---

