---
title: "Why &quot;gtk-menu-images&quot; = TRUE in ~/.gtkrc-2.0"
date: 2010-09-29
forum: Desktop Environments
---

### Post by lion.guo on 2010-09-29
ubuntu 10.10

when I start gtk app, always see like:
Gtk-Message: /home/USERNAME/.gtkrc-2.0:13: failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x9b7fc90)" of type `gboolean'
OR

..Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x82f3c90)" of type `gboolean'

In fact, my /.gtkrc-2.0 have some text like 
gtk-button-images=FALSE
gtk-menu-images=TRUE
gtk-enable-input-feedback-sounds=FALSE
gtk-enable-event-sounds=FALSE

BUT at  [http://live.gnome.org/GnomeArt/Tutorials/GtkThemes#The_gtkrc_File](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes#The_gtkrc_File), there are some note:
Note that TRUE and FALSE cannot be used in the theme, you can use 1 and 0 instead. (XXX is this OK?) 

so I changed TRUE/FALSE to 1/0, and these gtk messages disappeared.
 
I want to know, this right or wrong? Who make these configure value

---

### Post by lion.guo on 2010-09-29
seem it's made by lxappearance, long long ago.

---

