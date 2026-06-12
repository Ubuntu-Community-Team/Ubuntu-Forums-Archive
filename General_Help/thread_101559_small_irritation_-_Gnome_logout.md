---
title: "small irritation - Gnome logout"
date: 2005-12-10
forum: General Help
---

### Post by infoseeker on 2005-12-10
I have a small irritation that I was hoping that someone could help me with.  I don't get the option checkboxes (?) when logging out of gnome. See attached pic.  Its a hit or miss affair. Tried changing all sorts, (themes, etc.)....nothing will bring the options display back to normal :(

Thanks

---

### Post by magnusbb on 2005-12-10
This looked like my GNOME after using the gkt-qt standarization tool in KDE to make GNOME applications look more QT-ish.

Look for the gtk-qt package in Synpatic, and delete it. It only messes up GNOME. If you don't want to, I'm sure there is a config file hidden in your home directory you could remove.

---

### Post by infoseeker on 2005-12-10
Sorted out now thanks. Edited out as below in '~/.gtkrc-2.0'

> # This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

#          include "/usr/share/themes/Qt/gtk-2.0/gtkrc"

#          style "user-font"
#          {
#           	font_name="DejaVu Sans 9"
#          }
#          widget_class "*" style "user-font"

#          gtk-theme-name="Qt"
#          gtk-font-name="DejaVu Sans 9"


Its now back to normal. Thanks :)

This is possibly where it all started to go wrong:

[http://www.ubuntuforums.org/showthread.php?t=100049](http://www.ubuntuforums.org/showthread.php?t=100049)

---

