---
title: "Nautilus looks buggy and glitchy..."
date: 2010-12-21
forum: Desktop Environments
---

### Post by Danish989 on 2010-12-21
Whenever I open a folder using the gnome panel (places,) Nautilus runs and the window looks like it was designed when the first GUI was. It's all grey and doesn't match the rest of the GUI at all.

However, when I gksudo nautilus in Terminal, the window that opens looks perfectly fine and how it should look.

Also, the messed up nautilus does not have a bar with File, edit, and the other options... please help!

---

### Post by karthick87 on 2010-12-21
While nautilus is closed type the following in your terminal,
  ```
rm -R ~/.gconf/apps/nautilus
```  It will delete the folder with old settings.

---

