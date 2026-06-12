---
title: "gtk filechooser config"
date: 2013-08-03
forum: Desktop Environments
---

### Post by zensys on 2013-08-03
I use Ubuntu 12.10. Where can I change the sort order when selecting a file in the filechooser dialog. I read somewhere you could do that in the org section of gconf-editor but I do not see that section. Any suggestions highly appreciated.

---

### Post by vasa1 on 2013-08-03
> **zensys said:**
> I use Ubuntu 12.10. Where can I change the sort order when selecting a file in the filechooser dialog. I read somewhere you could do that in the org section of gconf-editor but I do not see that section. Any suggestions highly appreciated.
I looked at ~/.config and found a subfolder called "gtk-2.0: which has a "gtkfilechooser.ini" file:
```
[Filechooser Settings]
LocationMode=path-bar
ShowHidden=false
ShowSizeColumn=true
GeometryX=257
GeometryY=81
GeometryWidth=852
GeometryHeight=630
SortColumn=name
SortOrder=ascending
StartupMode=recent
```

For gtk3, the file to edit probably is ~/.config/gtk-3.0/settings.ini. You can read more about settings.ini here: 
[https://developer.gnome.org/gtk3/3.1/GtkSettings.html](https://developer.gnome.org/gtk3/3.1/GtkSettings.html)

---

### Post by zensys on 2013-08-12
> **vasa1 said:**
> I looked at ~/.config and found a subfolder called "gtk-2.0: which has a "gtkfilechooser.ini" file:
```
[Filechooser Settings]
LocationMode=path-bar
ShowHidden=false
ShowSizeColumn=true
GeometryX=257
GeometryY=81
GeometryWidth=852
GeometryHeight=630
SortColumn=name
SortOrder=ascending
StartupMode=recent
```

For gtk3, the file to edit probably is ~/.config/gtk-3.0/settings.ini. You can read more about settings.ini here: 
[https://developer.gnome.org/gtk3/3.1/GtkSettings.html](https://developer.gnome.org/gtk3/3.1/GtkSettings.html)

Thx vasa1 but I do not have a gtk directory in .local. In fact I do not have a gtkfilechooser file on my system (as checked with locate).

---

### Post by macsym on 2014-03-21
Hello,

I am on Ubuntu 12.04-64 LTS and I am trying to sort by modified date by default (instead of name) for the file chooser dialog window.

- Like Zensys, I have no "gtk-2.0" or "gtk-3.0" or "gtksomething..." directory in ~/.config
- I also tried the dconf-editor method described at [http://askubuntu.com/questions/83552/how-do-i-set-the-default-sort-order-in-open-file-dialog-to-name](http://askubuntu.com/questions/83552/how-do-i-set-the-default-sort-order-in-open-file-dialog-to-name) but it didn't change anything
- I found and edited ./usr/share/glib-2.0/schemas/org.gtk.Settings.FileChooser.gschema.xml but it didn't work either...

Any solution??

Thanks for any help

---

