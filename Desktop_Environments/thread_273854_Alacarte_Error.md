---
title: "Alacarte Error"
date: 2006-10-08
forum: Desktop Environments
---

### Post by myfmelo on 2006-10-08
Hi everyone,

I'm trying to execute alacarte without any success. The problem started after I created a new item for NetBeans on the menu. Since then the following error appears:

Any idea? Thanks in advance.

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
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
    __parse(doc, filename, tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 571, in __parse
    parent.Rules.append(Rule(child.tagName, child))
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 284, in __init__
    self.compile()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 290, in compile
    exec("""
  File "<string>", line 6
    elif (menuentry.DesktopFileID == 'file:---home-user-Desktop-netbeans5.5rc1.desktop
      ^
SyntaxError: EOL while scanning single-quoted string

---

