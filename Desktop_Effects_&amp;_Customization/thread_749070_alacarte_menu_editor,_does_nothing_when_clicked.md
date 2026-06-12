---
title: "alacarte menu editor, does nothing when clicked"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by Greenducky on 2008-04-08
Hey guys when i right click on the ubuntu start button and click edit menu nothing happens.
also when i hit alt + f2 and then type alacarte & nothing happens.
also when i go to menu preferences and then click mainmenu nothing happens.

by the way if you are reading this and are unaware of what i am talking about. all three things are trying to launch the same
program called alacarte. alacarte is a menu editor to edit the programs that you see and dont see in the menu

This is what it lookes like when i try it in a terminal.
____________________________________________________________________________________________________________________________-

mint@mint-desktop:~$ alacarte &
[1] 31504
mint@mint-desktop:~$ Traceback (most recent call last):
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
File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 207, in parseFile
parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 13, column 52

____________________________________________________________________________________________________________________


Please help me.
I tried uninstalling it from synaptic and then reinstalling it and then reloading plugins on the  menu. and nothing. i've restarted x and rebooted.
even when i try to change the session to safe gnome mode. and log inn it still dont work.
it worked fine earlier today, only thing i did between now and then is install adobe cs2 in wine doors.
I hope someone can make some sense of this.

---

### Post by jrib on 2008-04-08
see if you receive the same error on a fresh new user account

---

