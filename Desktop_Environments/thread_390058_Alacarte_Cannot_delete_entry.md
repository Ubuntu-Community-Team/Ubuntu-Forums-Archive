---
title: "Alacarte: Cannot delete entry"
date: 2007-03-21
forum: Desktop Environments
---

### Post by SgtMuffles on 2007-03-21
Hi. So I had gvim installed and an entry was added in alacarte under accessories. Can't remember whether I somehow did this manually or if the installer did this. However, I uninstalled it and as a housekeeping measure would like to remove it from alacarte altogether. I unchecked it, which does half that job, but when I right-click the "delete" option presented to me is greyed out. Any ideas as to what I can do?

---

### Post by ardchoille42 on 2007-03-21
> **SgtMuffles said:**
> Hi. So I had gvim installed and an entry was added in alacarte under accessories. Can't remember whether I somehow did this manually or if the installer did this. However, I uninstalled it and as a housekeeping measure would like to remove it from alacarte altogether. I unchecked it, which does half that job, but when I right-click the "delete" option presented to me is greyed out. Any ideas as to what I can do?

Most likely the installer added this menu item. The menu system, and alacarte, get those entries from /usr/share/applications. You can uncheck it, which removes it from your menus, but if you must delete this menu item altogether, you can delete the appropriate item in /usr/share/applications. If you add an item to the menus manually, using alacarte, the menu item is more likely in ~/.local/share/applications.

---

