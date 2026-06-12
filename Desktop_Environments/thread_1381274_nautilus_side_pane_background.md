---
title: "nautilus side pane background"
date: 2010-01-14
forum: Desktop Environments
---

### Post by Post Monkeh on 2010-01-14
is there any way to change this?

i can change the main folder backgrounds ok by opening the backgrounds and emblems menu and dragging the background i want across, but this can't be done to the side panel (with the exception of the info setting, it seems to be the only one that can be set in this way though.)

even if i could just change the colour of it it would be helpful

---

### Post by Post Monkeh on 2010-01-23
anyone?

---

### Post by VCoolio on 2010-01-23
It's a theme setting. Either edit your themes gtkrc file or edit ~/.gtkrc-2.0 (create it if it doesn't exist yet) and add this line:

GtkTreeView::even_row_color   = "#FF0000"

In .gtkrc-2.0 you can just add this line; in $THEME/gtkrc you need to find the proper place for it.
#ff0000 is to be replaced with 
1. proper color code within " ", or 
2. name within " " (the basic ones like red, blue, green are recognized), or 
3. @fg_color or something like that if your theme has these colors specified somewhere on top of the gtkrc file; this way you can change it using the colors tab in appearance.

Remember that this line, obviously, also influences the treeviews, for example the lists in open / save dialogs. If that makes things ugly, specify a matching odd_row_color.

---

### Post by Post Monkeh on 2010-01-23
theme is customised so the only refernece to it is in my home folders .themes dir, and it has no gtkrc file

i added the line you suggested to my ~/.gtkrc-2.00 file, which now looks like 

> include ".gtkrc-2.0-gnome-color-chooser"
GtkTreeView::even_row_color = "#FF0000"

i deselected the entry field background colour (the one which i found changed the colour of the side pane, but also several other things which isn't ideal) but my side pane is just reverting to white, even after a reboot.

---

### Post by VCoolio on 2010-01-23
Sorry, hadn't thought it through. Try to add this instead:

```
style "treeview-mod"
{   
    GtkTreeView::even_row_color   = "#FF0000"
}
widget_class "*.<GtkTreeView>*"                 style "treeview-mod"
```

Don't reboot, just log out and back in, or change theme and back.

---

### Post by VCoolio on 2010-01-23
Found it! Instead of the last line (widget_class etc) do

widget "*NautilusNavigationWindow*" style "treeview-mod"

---

### Post by Post Monkeh on 2010-01-23
good man

---

