---
title: "Main menu wont work?"
date: 2009-03-12
forum: General Help
---

### Post by n3gative12 on 2009-03-12
I was using acidrip to preview a dvd before I ripped it, and when I closed the program the audio kept playing. I tried opening the system monitor to end the process, but every time i tried to change to the processes tab the system monitor closed itself. On top of that, my applications menu had disappeared. The menu is technically there, just empty (a small square shows up below the panel).[IMG]http://www.filesavr.com/menu_3[/IMG]
The pictures, videos, etc. are also gone from my places menu.
Does anybody know a way to fix this? I tried using the main menu editor in preferences, but it won't start up, even after I purged/reinstalled it.

---

### Post by mastahyeti on 2009-03-12
I am going to assume that you restarted the system. If not, do so, that will probably fix it. If this doesn't help, you can get to something similar to the system monitor by opening the terminal and typing "top". You will see all the processes and their pids. To kill a process in the command line just type "sudo kill [pid]". If you are having a hard time getting to the terminal because of your menu problem you might try holding <alt>+F2 and then type "gnome-terminal" to launch the terminal. Alternatively you can get to the tty by holding down <CTRL>+<ALT>+F1. For your purposes this should work as well.

---

### Post by drs305 on 2009-03-12
Try opening for editing from from the command line/terminal. 

If you type "**alacarte**" in a terminal it should open the menu for editing. If it opens, highlight Applications in the left pane and see if there are any apps listed/ticked in the right pane. If there are, you can enable any listed in the right pane by ticking them.

---

### Post by n3gative12 on 2009-03-12
> **drs305 said:**
> Try opening for editing from from the command line/terminal. 

If you type "**alacarte**" in a terminal it should open the menu for editing. If it opens, highlight Applications in the left pane and see if there are any apps listed/ticked in the right pane. If there aren't, you can enable any listed in the right pane by ticking them.
I tried that, but i got an error output:```
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
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0



```
and the editor doesn't open up. Even after reinstalling, it won't work... I'm not sure why.

---

