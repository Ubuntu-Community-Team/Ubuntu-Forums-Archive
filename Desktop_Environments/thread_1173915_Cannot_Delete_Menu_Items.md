---
title: "Cannot Delete Menu Items ?"
date: 2009-05-30
forum: Desktop Environments
---

### Post by celem on 2009-05-30
When I launch "Edit Menus" and try to delete a menu item nothing happens. Specifically I was trying to delete those items in the attached screenshot but when I highlight the item and press delete, nothing happens. These particular items are in ~/.config/menus/applications-merged instead of the primary menu folder.

Any ideas?

---

### Post by Brandon Williams on 2009-05-30
alacarte is not very good at deleting items from the menus. It can cause problems for your whole desktop environment if you delete the wrong items (not true in this case, but true in others). If it's not enough to just make the items invisible in the menu, then I suggest that you edit the .menu files under .config/menus/... and/or the .desktop files under .local/share/applications directly, rather than relying on alacarte. If it can't be deleted by removing something from either a .menu file or by deleting a .desktop file, then I recommend that you let it show up in the alacarte menu.

---

### Post by Jimmynemo2 on 2009-05-30
I can agree there- I simply uncheck most items from my alacarte, but my delete tends to either not delete them, or put them back. Not sure why....

---

