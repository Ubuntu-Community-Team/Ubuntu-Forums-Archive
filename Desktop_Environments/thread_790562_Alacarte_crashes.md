---
title: "Alacarte crashes"
date: 2008-05-11
forum: Desktop Environments
---

### Post by wilkenw on 2008-05-11
I am running Hardy Heron with all the latest updates and am encountering a major problem with the alacarte menu manager.  When using this application yesterday to remove two or three items from my applications menu, alacarte wiped out my entire applications menu.  Now, when I attempt to execute it, alacarte crashes with the following debug information:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 35, column 22

While I know little about python, the info above indicates that alacarte has created faulty xml in some text file.  But which file?  Importantly, uninstalling, then re-installing the gnome desktop does not solve the problem.  In short, I lack an applications menu and am unable to recreate it.

---

### Post by wilkenw on 2008-05-12
Solved problem by restoring old applications.menu file in home .config folder

---

### Post by Tye on 2008-05-14
What steps did you take to fix the problem?

As i have had it happen to me

---

