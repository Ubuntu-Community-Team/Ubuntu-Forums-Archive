---
title: "Wubi uninstall error."
date: 2009-04-27
forum: General Help
---

### Post by Name141 on 2009-04-27
I installed Xubuntu by Wubi.  Then uninstalled it, however when I boot the computer up I still have the screen asking for Xubuntu or Windows OS ?

Will I have to use the Windows XP disk recovery console to run "fixmbr" ? or is there a supplier option for me?

---

### Post by blazemore on 2009-04-27
In Windows, press WinKey + R to bring up the Run dialogue.

Type *msconfig* and hit Enter.

Click on the Boot tab.
Here you can see the different items in the boot menu, and you can reorder them and delete them.

---

### Post by Name141 on 2009-04-27
I think I found it, the "C:\wubildr.mbr = "Xubuntu" " ?

---

### Post by blazemore on 2009-04-27
I would definately use msconfig first, before messing with actual files.

If it's not there, then by all means try deleting whatever you want, but I accept to responsibility for your actions.

---

