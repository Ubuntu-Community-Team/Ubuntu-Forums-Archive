---
title: "Applications / System Menus are empty"
date: 2010-09-26
forum: Desktop Environments
---

### Post by ipsi on 2010-09-26
In trying to fix issues I have been having with my display, I seem to have inadvertently removed all applications from my menu, which is rather annoying. I'm not sure how. I've attached a couple of screenshots to display this.

When trying to access the 'Main Menu' option from the Gnome Control Center, I get the following error in the command line:

```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 48, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 48, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 1, column 1
```

Anyone have any idea what I've done, and how I can fix it?

---

### Post by sikander3786 on 2010-09-26
Type,

```
rm -r ~/.gconf/apps/panel
```

It will remove all the settings for your panels and hopefully, bring back the default menus.

---

### Post by ipsi on 2010-09-26
Thanks, but that doesn't appear to have helped. I moved it to panels.OLD instead of deleting it, though (I doubt that makes a difference, but hey).

Unfortunately, while it has reset my panel, the Applications and System menus are still blank, as per my previous screenshots. Guess that means I've buggered something rather more important then?

Any more suggestions? Where would I likely find the system-wide configuration? I should probably create another account to see if it's a system-wide problem.

---

### Post by ipsi on 2010-09-26
Ok, I created a new account to test, and that was created with the proper menus and everything, so I've obviously removed a different file somewhere.

---

### Post by ipsi on 2010-09-26
Found the solution here:

[http://ubuntuforums.org/showpost.php?p=4405544&postcount=4](http://ubuntuforums.org/showpost.php?p=4405544&postcount=4)

```
cd /home/user/.config/
rm -R menus/
```

---

### Post by sikander3786 on 2010-09-26
Most of the configuration files from home directory, when deleted, they reset the settings for the concerned application and the files themselves are recreated when that application is run again.

Not to worry about that until you didn't delete something outside of the home directory and more importantly be careful when deleting or modifying something as being "root".

---

