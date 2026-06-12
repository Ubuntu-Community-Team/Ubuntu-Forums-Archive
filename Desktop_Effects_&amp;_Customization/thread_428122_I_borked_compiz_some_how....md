---
title: "I borked compiz some how..."
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by hanzomon4 on 2007-04-30
I borked compiz somehow, not sure how exactly...

I did play around with installing v0.5 but I reverted back. I've purged, uninstalled, reinstalled, tried different versions and nothing. I think it has something to do with settings somewhere. Well here's the errors I get:```
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_maximized"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_2"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_4"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_6"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_8"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_11"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_left"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_right"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_up"
Window manager warning: "" found in configuration database is not a valid value for keybinding "move_to_workspace_down"
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize_vertically"
Window manager warning: "" found in configuration database is not a valid value for keybinding "maximize_horizontally"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_3"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_7"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_8"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_10"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_11"
Window manager warning: "" found in configuration database is not a valid value for keybinding "switch_to_workspace_left"

```

Any ideas?

---

### Post by kvonb on 2007-04-30
The settings are stored in the Gconf database, a nasty little Window-esque throwback thing!

You can edit those settings by pressing <alt><f2> and typing:

gconf-editor

Into the box and running it.

The compiz settings are under Apps->Compiz, you could try changing all the ones in that list that give you errors.

Unfortunately I don\t think you can just delete them from there.

Also be careful, you could easily mess something up!

---

### Post by hanzomon4 on 2007-04-30
I found the problem apparently a package I installed for v0.5(compiz-config-gnome) screwed up my settings and nothing I've tried has fixed whatever this package changed. The only solution was to reinstall v0.5.

---

