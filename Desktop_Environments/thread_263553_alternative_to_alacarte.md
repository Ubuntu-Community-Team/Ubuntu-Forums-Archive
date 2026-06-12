---
title: "alternative to alacarte"
date: 2006-09-23
forum: Desktop Environments
---

### Post by visvak on 2006-09-23
since two or three days, alacarte menu editor has not been opeining at all.

it used to be hell slow before, but i read all the complaints on the forums by other users about alacarte being slow and i figured it was just natural.

then 2 days back it just stoped launching. when i click the icon it shows "the launching alacarte" in the taskbar and then after a while it just diappears and dosent launch.

ive reinstalled several times. it still dosent work. is there a fix for this problem ?

otherwise, is there an alternative to alacarte ?

---

### Post by skymt on 2006-09-23
What error do you get if you run "alacarte" in a terminal?

---

### Post by visvak on 2006-09-23
alacarte in terminal says : 


```
(alacarte:7412): Gdk-WARNING **: locale not supported by Xlib

(alacarte:7412): Gdk-WARNING **: cannot set locale modifiers

(alacarte:7412): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:7412): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:7412): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed

(alacarte:7412): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:7412): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:7412): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 26, in ?
    main()
  File "/usr/bin/alacarte", line 23, in main
    GnomeFront()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 72, in __init__
    self.loadMenus()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 205, in loadMenus
    self.sys_handler = MenuHandler('settings.menu', self.options)
  File "/usr/lib/python2.4/site-packages/Alacarte/PyXDGMenuHandler.py", line 27, in __init__
    xdg.MenuEditor.MenuEditor.__init__(
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 40, in parse
    self.menu = parse(menu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 859, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1036, in __addFiles
    self.__addFiles(dir, os.path.join(subdir,item), prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1028, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'utf8' codec can't decode byte 0xb5 in position 17: unexpected code byte

```

---

