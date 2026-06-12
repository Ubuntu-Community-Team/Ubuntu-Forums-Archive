---
title: "&quot;Open as administrator&quot; in menus"
date: 2008-11-10
forum: Desktop Environments
---

### Post by DaSilva on 2008-11-10
Is it possible to add an entry like "Open as administrator" to the context menu (right click) in menus like "Applications" and "System"? I know it is possible in nautilus with a simple script but I want to have something like this as an option in the menus, too.
Thanks in advance.

---

### Post by pietjanjaap on 2008-11-10
Is in the synaptic package manager, but i do not know the name, so if somebody could help.

---

### Post by IshikawaNakano on 2008-11-10
You might be able to start the program with *gksudo* from the file manager.

You can do this to start applications as root. I use wireshark as an example but you can do this with other programs:
Right click on the menu an click Edit Menus. Create a second menu item that is the same as the old one. Change the name to something else (i.e. wireshark (root) instead of wireshark). Add *gdsudo* to the beginning of the command.

---

### Post by DaSilva on 2008-11-10
Thanks, I will try it :)

---

