---
title: "Alacarte Menu Editor wont start"
date: 2006-09-26
forum: Desktop Environments
---

### Post by villindesign on 2006-09-26
Hello,
I recently wanted to add something to my menu, but when I clicked on Alacarte menu editor, it wouldn't start. I tried running it from the command line, and this is what I got:
```
britt@britt-laptop:~$ alacarte

(alacarte:14809): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:14809): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:14809): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 26, in ?
    main()
  File "/usr/bin/alacarte", line 23, in main
    GnomeFront()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 72, in __init__
    self.loadMenus()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 201, in loadMenus
    self.app_handler = MenuHandler('applications.menu', self.options)
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
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 26-28: invalid data

```

I can add program launchers to the panel on my desktop, but I can't add anything to the menu. Does anyone know how to correct this?
Thanks-

---

### Post by aysiu on 2006-09-26
Does [this](http://ubuntuforums.org/showthread.php?t=142868&highlight=alacarte) help?

---

### Post by villindesign on 2006-09-26
No, for some reason that did not work for me. I think it is something to do with Menu.py though...

---

