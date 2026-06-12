---
title: "Remove right Click Menu for Desktop"
date: 2008-11-16
forum: Desktop Environments
---

### Post by Benismyhorse on 2008-11-16
Hi everyone, working on a Ubuntu Thin Client and was hoping if anyone knew how to disable or remove or edit the right click menu on the Desktop.

Thanks

---

### Post by aaaantoine on 2008-11-16
One way I know of is to disable the Nautilus desktop entirely.  Run the command... ```
gconf-editor
``` ...then go to key /apps/nautilus/preferences/show_desktop and uncheck it.

If that doesn't quite meet your needs, there are more options you can play with in /apps/nautilus.

---

### Post by Benismyhorse on 2008-11-16
Hi, am using Gconf-editor for all my lockdowns but I need to have a few icons on the Desktop is there any way I could do this.

Thanks

---

### Post by aaaantoine on 2008-11-16
If you find out, let me know.

---

