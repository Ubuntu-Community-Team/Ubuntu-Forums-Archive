---
title: "bookmarks in file browser and submenu in panel gone after disk running out of  space"
date: 2009-05-19
forum: General Help
---

### Post by raj11 on 2009-05-19
[FONT=Trebuchet MS][FONT=Times New Roman][SIZE=3]I am using ubuntu 9.04 in wubi installation. yesterday my disk in computer was running out of space and after that bookmarks in file browser gone. 
When I click on Application in a panel, no sub menus appeared. I can access sub menus in places and system from the panel.

[/SIZE][/FONT][/FONT]

---

### Post by chiefbutz on 2009-05-19
Trying going to ```
System > Preferences > Main Menu
``` and ensuring that the different menus have a check mark to the left of them so that they will be displayed.

---

### Post by raj11 on 2009-05-19
When I click on system > Preference > main menu, nothing appears.  I have tried 4 - 5 times, but nothing appears after a click on main menu.

---

### Post by chiefbutz on 2009-05-19
Try pressing Alt + F2 and typing in "xterm"

Then type this into the command prompt that shows up "alacarte"

If there are any errors post those back please.

---

### Post by asmoore82 on 2009-05-19
> **raj11 said:**
> [FONT=Trebuchet MS][FONT=Times New Roman][SIZE=3]I am using ubuntu 9.04 in wubi installation. yesterday my disk in computer was running out of space and after that bookmarks in file browser gone. 
When I click on Application in a panel, no sub menus appeared. I can access sub menus in places and system from the panel.

[/SIZE][/FONT][/FONT]

This happened to me as well when I accidentally filled my drive - just the "Bookmarks" part
I just created them again - CTRL+D if you want to get fancy with it.

[SIZE="5"][COLOR="Blue"]My 1000th Post![/COLOR][/SIZE]

---

### Post by raj11 on 2009-05-19
I have type as you mentioned in terminal. Not sure if I have done it correctly. I am posting the results.
------
raj@ubuntu:~$ alacarte
/home/raj/.gtkrc-2.0:20: error: invalid string constant "#3D1919", expected valid string constant
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
-----
Thanks

---

### Post by asmoore82 on 2009-05-20
> **raj11 said:**
> I have type as you mentioned in terminal. Not sure if I have done it correctly. I am posting the results.
------
raj@ubuntu:~$ alacarte
[COLOR="Red"]/home/raj/.gtkrc-2.0:20[/COLOR]: error: invalid string constant "#3D1919", expected valid string constant
-----
Thanks

It looks like [COLOR="Red"]that[/COLOR] file is corrupt,
you could try renaming it to a backup and see if that helps

```
mv .gtkrc-2.0 .gtkrc-2.0.backup
alacarte
```

---

### Post by raj11 on 2009-05-20
I have typed as you mentioned but still it shows an error. 
---
raj@ubuntu:~$ mv .gtkrc-2.0 .gtkrc-2.0.backup
raj@ubuntu:~$ alacarte
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
-----

---

### Post by asmoore82 on 2009-05-20
> **raj11 said:**
> I have typed as you mentioned but still it shows an error. 
---
raj@ubuntu:~$ mv .gtkrc-2.0 .gtkrc-2.0.backup
raj@ubuntu:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
-----

sounds like more corruption here -
but I couldn't venture a guess as to
whether it is in alacarte or the python library itself...

are you using the new ext4 filesystem?
a full drive may be one of its weaknesses

---

### Post by raj11 on 2009-05-20
I am using a wubi installation. 
Is it possible to get it back, If i remove and install a panel again?

---

