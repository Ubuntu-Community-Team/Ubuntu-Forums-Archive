---
title: "Uninstalling gnome-shell and getting default shell back"
date: 2010-02-15
forum: Desktop Environments
---

### Post by lsuengineer on 2010-02-15
Hello,
I recently installed gnome-shell and set it and mutter as my defaults. Under gconf-editor, "windowmanager" is set to "gnome-shell." My question is what is the default gnome window manager?

Thanks

---

### Post by xtracool_protik on 2010-02-16
Default window manager for gnome is metacity(gtk), not sure if that answered ur question -- I couldn't understand it completely

---

### Post by aristoddler on 2010-02-19
I also replaced "windowmanager" with "gnome-shell" in gconf-editor.  Now Gnome shell is moving impossibly slow and I have no idea how to return to the normal panel.. help )

---

### Post by ashikrobi on 2011-03-19
U can try to uninstall gnome-shell from ubuntu software center. But without it u can get default shell.

alt-F2
gconf-editor
desktop>gnome>session>required_component
right click windowmanager and click on edit key.
Now on value box you need to type gnome-wm. Log out and log back in. Thats all.

I believe if u try compiz or metacity instead of gnome-wm, it will work also.
Good luck.

---

