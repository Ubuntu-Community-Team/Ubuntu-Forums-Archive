---
title: "AGM can't work"
date: 2008-12-28
forum: Desktop Environments
---

### Post by hazenvnn on 2008-12-28
I installed advancedgnomemenu but it can't work, it shows these lines when I try to start it from terminal
>  advancedgnomemenu
Running installed agm, modifying PYTHONPATH.
/usr/lib/python2.5/site-packages/AGM/AGM_Main_Window.py:198: GtkWarning: Attempting to add a widget with type GtkImage to a GtkEventBox, but as a GtkBin subclass a GtkEventBox can only contain one widget at a time; it already contains a widget of type GtkImage
  self.EBox.add(gtk.Image())
loading: Favorite Apps plugin
loading: Search plugin
loading: Gnome menu plugin
loading: Place plugin
loading: Recently used files plugin
loading: Browse files plugin
loading: More places plugin
loading: Logout plugin
loading: Search in Gnome menu
loading: Bookmarks plugin
loading: Install apps throught synaptic plugin
loading: Search in home
None
Traceback (most recent call last):
  File "./AGM.py", line 91, in <module>
    AGM(top_buttons=False)
  File "/home/marco/Programmazione/advancedgnomemenu/src/AGM/AGM_Main_Window.py", line 103, in __init__
  File "/home/marco/Programmazione/advancedgnomemenu/src/AGM/AGM_Main_Window.py", line 240, in setObjects
  File "/home/marco/Programmazione/advancedgnomemenu/src/AGM/AGM_menu.py", line 49, in __init__
  File "/home/marco/Programmazione/advancedgnomemenu/src/AGM/AGM_menu.py", line 86, in refresh
  File "/home/marco/Programmazione/advancedgnomemenu/src/AGM/AGM_menu_button.py", line 50, in __init__
  File "/home/marco/Programmazione/advancedgnomemenu/src/AGM/AGM_utils.py", line 14, in getPixbufFromName
TypeError: argument of type 'gtk.gdk.Pixbuf' is not iterable
bye bye

 Also, I can't start emerald, tried to use emerald -replace but there is nothing change.

---

### Post by brus46 on 2009-02-10
Which version you have installed? try update to agm 0.8.3-2 ;)

---

