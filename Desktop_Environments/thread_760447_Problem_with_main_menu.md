---
title: "Problem with main menu"
date: 2008-04-20
forum: Desktop Environments
---

### Post by cikson on 2008-04-20
I have problem with main menu on Ubuntu 7.10 I can't edit main menu neither run programs from main manu only I can run applications is from trminal.
Please help!

---

### Post by Vermind on 2008-04-20
Hello,
Is this a livecd or on hard disk? Do You mean graphical terminal like gnome-terminal or outside X?
I take it that You can reach X anyway if You see the Gnome panel. Maybe Your Gnome panel is dead? You could try to start gnome-terminal into the X session by running ```
DISPLAY=:0 gnome-terminal
``` outside X. Then try to ```
killall -s TERM gnome-panel
``` and see if the panel works after that. If the panel has broken down recently, backing up the whole gnome configuration and restarting X might work (do this in home directory):
```
mkdir gnome-backup; mv .gconf .gnome2 gnome-backup
``` Then press ctrl-alt-backspace to restart X.

---

### Post by cikson on 2008-04-20
It is not problem in terminal or Gnome in general. Problem is when I try to click on Applications on Gnome panel it does not start or System -> preferences -> Main Menu

---

### Post by Steve1961 on 2008-04-20
> **cikson said:**
> It is not problem in terminal or Gnome in general. Problem is when I try to click on Applications on Gnome panel it does not start or System -> preferences -> Main Menu

Try running alacarte from the command line and post the output

---

### Post by cikson on 2008-04-20
```
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
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

```

---

### Post by Vermind on 2008-04-20
Hello,
You could try to move Your applications menu out of the way and see if that helps.
Someone had a similar crash with alacarte:
[Alacarte random crash]("http://http://www.daniweb.com/forums/thread109883.htm")
It would appear that alacarte cannot read the menu file correctly.
Moving the menu out of the way:
```
mv .config/menus/applications.menu  .
```
If this fixes the issue, then You can try fixing the menu file and moving it back, or adding Your custom entries again.

---

### Post by cikson on 2008-04-20
It works! Thanks:)

---

