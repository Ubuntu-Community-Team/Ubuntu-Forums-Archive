---
title: "Menu editing refusing to run"
date: 2008-02-01
forum: Desktop Environments
---

### Post by fcigoi on 2008-02-01
Gents,

Since I installed 7.10, when I try to either run System > Preferences > Main Menu or right-click Applications and selecting Edit Menus, the system fumbles around for a while, brings up an icon on the taskbar for a few seconds and then everything disappears again.
The bottom line is that I cannot edit my menus, i.e. add application launchers.
Has anyone had the same problem and managed to solve it ?

---

### Post by Vixis on 2008-02-01
run in console
```
alacarte
```
and post errors.

---

### Post by fcigoi on 2008-02-05
There you go.....

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
IOError: [Errno 13] Permission denied: '/home/fcigoi/.config/menus/applications.menu'

---

### Post by liniaal on 2008-02-05
is fcigoi your first & only user account? have you accidentally touched something in your homedir as 'root'?

---

### Post by fcigoi on 2008-02-08
Yes, fcigoi is the only user. 
As regards touching something as root I don't think so but...sometimes strange things happen

---

### Post by fcigoi on 2008-02-09
Problem solved. I chowned menu to fcigoi and it all works ok. Thanks for the help

---

### Post by Cew27 on 2008-02-13
how did you fix this ?

---

