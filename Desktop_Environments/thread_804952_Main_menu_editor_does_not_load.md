---
title: "Main menu editor does not load"
date: 2008-05-23
forum: Desktop Environments
---

### Post by wkdude18 on 2008-05-23
Most of the applications in the applications menu disappeared, so when I tried to load the menu editor and click revert, the program crashed. Now it will not load. this is what happened in the terminal after typing alacarte:
alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 44, in __loadMenus
    self.applications.dom = xml.dom.minidom.parseString(util.getUserMenuXml(self.applications.tree))
  File "/usr/lib/python2.5/site-packages/Alacarte/util.py", line 197, in getUserMenuXml
    name = tree.root.get_menu_id()
AttributeError: 'NoneType' object has no attribute 'get_menu_id'
Does anyway understand this? (I suck at command line)

---

### Post by Romanovzky on 2008-09-17
Same problem here... How did you solve it?

---

