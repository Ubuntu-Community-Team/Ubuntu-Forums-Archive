---
title: "Edit Menus Missing"
date: 2009-05-19
forum: General Help
---

### Post by Don DeGregori on 2009-05-19
Using Ubuntu 8.04.1 LTS. Can't see Edit Menus off of top panel. Right clicking, the phrases "Edit Menus" is there, but left clicking on "Edit Menus" yields nothing. It worked at one time. Can I get it back?

Don

---

### Post by Legace on 2009-05-19
> **Don DeGregori said:**
> Using Ubuntu 8.04.1 LTS. Can't see Edit Menus off of top panel. Right clicking, the phrases "Edit Menus" is there, but left clicking on "Edit Menus" yields nothing. It worked at one time. Can I get it back?

Try to execute **alacarte** from Terminal and post any errors you get..

---

### Post by Don DeGregori on 2009-05-19
alacarte gives me this below
Don


 donde@donde-desktop:~$ alacarte
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
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/donde/.config/menus/applications.menu'
donde@donde-desktop:~$

---

