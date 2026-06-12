---
title: "applications submenus gone..."
date: 2009-09-20
forum: Desktop Environments
---

### Post by 78ufzniyE4 on 2009-09-20
Helo this is the second time im using ubuntu fourms and had a serious problem i have been told to run sudo apt-get clean and then
when i click on the applications menu to start up the terminal there only came a small white box.

This was very odd to me because lots and lots of people ran sudo apt-get clean and had no problems. I tried oppening menu editor (acarlate)from the terminal and system --> preferences --> menu editor, but it did not apear. 

When i ran it from the terminal i got this error:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
aaronvarghese@tedy132:~$
:(

looks like im missing a python library.

---

### Post by 78ufzniyE4 on 2009-09-20
anyone...

---

### Post by drs305 on 2009-09-20
If you right click on the Applications bar, do you have an option to "Edit menus"? If so, does the "Revert" button appear and does selecting it restore your menus?

You should also be able to get to the "Revert" button via System, Preferences, Main Menu.

---

### Post by 78ufzniyE4 on 2009-09-21
nope thats not it i figured it out by running    rm ~/.config/menus/applications.menu or if it doent work type  rm/home/<your username>/.config/menus/applications.menu

thanks for your help and btw how do you get coffey instead of beans :popcorn: yaaaaaaaa!!!!! i fixed it! :guitar::guitar::guitar::-D

---

### Post by drs305 on 2009-09-21
> **linuxbrother11 said:**
> btw how do you get coffey instead of beans 

It's something the mods came up with - just for fun. The 'beans' and 'coffee' images change based on post count. It's not a reason to make "me too" posts but you'll see them change as your post count mounts.

---

