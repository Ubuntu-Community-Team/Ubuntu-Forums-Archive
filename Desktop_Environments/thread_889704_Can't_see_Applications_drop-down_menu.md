---
title: "Can't see Applications drop-down menu"
date: 2008-08-14
forum: Desktop Environments
---

### Post by perter.alpha on 2008-08-14
I was doing something with wine on Ubuntu 8.04.

But suddenly it happens:

When I click 'Applications', there's no drop-down menu containing applications list.

Also, I can't launch System-Preference-Main Menu.
No response at all, when I click 'Main Menu'

Help me plz !

Thanks a lot.
WS

---

### Post by sayakb on 2008-08-14
Press Alt+F2 and type **alacarte**. Then enable the Applications menu components from there..

---

### Post by perter.alpha on 2008-08-14
Thanks a lot.

I typed 'alacarte' and founded no response.
Furthermore, I typed 'alacarte'in xterm window,
and got a following message:

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


Is there something wrong with my phython ?

Thanks
WS

---

### Post by Timpotten on 2008-12-31
Right click panel where the drop-down used to be
Ignore the top two options, and scroll down to Menu Bar and select it!

---

### Post by colbobs on 2009-01-01
I tried this and the solutions offered in another thread with no success.

[http://ubuntuforums.org/showthread.php?t=926660](http://ubuntuforums.org/showthread.php?t=926660)
[http://ubuntuforums.org/showthread.php?t=926592](http://ubuntuforums.org/showthread.php?t=926592)  (this thread)


I experienced some significant problems with networking not so long ago and a group of synaptec package updates fixed it.  I think this new fault is in fact a hang-on from that last set of issues.

All other functioning is as before with no problems to report other than this applications menu problem.
Anyone with any more tips on this one please?
Happy New Year too.

---

### Post by marcurius on 2009-10-18
i know it's late, but here's posible solution...

thanks to Pete Ryland for this

```
$ rm -f ~/.config/menus/applications.menu
$ alacarte
```

---

### Post by francoise_peace on 2009-12-06
Same problem

I could have back Applications menu but neither Alacarte nor Edit Menus doesn't work and I do not have Preferences menu neither Administration Menu in System :(

mkdir ~/Documents/backup
mkdir ~/Documents/backup/dot-config/
mkdir ~/Documents/backup/dot-config/menus
sudo cp ~/.config/menus/* ~/Documents/backup/dot-config/menus
rm -f ~/.config/menus/applications.men
alacarte

[http://forum.ubuntu-fr.org/viewtopic.php?pid=3120073](http://forum.ubuntu-fr.org/viewtopic.php?pid=3120073)

alacarte is still an error message in gnome-terminal

---

