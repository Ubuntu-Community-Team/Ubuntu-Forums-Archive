---
title: "Progam Trouble..."
date: 2006-02-26
forum: Desktop Environments
---

### Post by Swiss on 2006-02-26
There are several programs that when I start it, it will show the "loading" dialog, but when its done loading, the program disappears! Its maddening!

I am trying to start this one in particular (sp?) : Applications Menu Editor

---

### Post by Perfect Storm on 2006-02-26
Try 
```
smeg
```

If you have trouble starting programs, try run them in the terminal. You'll see error output which tell you what's wrong.

---

### Post by Swiss on 2006-02-26
I tried running it in term... Same thing....

Here is the smeg output:

Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __init__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 30, in parse
    for line in file(filename,'r'):
IOError: [Errno 13] Permission denied: '/usr/share/applications/dvdrip.desktop'

---

### Post by Vietman on 2006-02-26
Sounds like you used the automatix script. Applications menu editor is trying to read your .desktop files. You need to edit a few of those files that cause the error, and add read permission to groups and others. (They were installed without permissions for your user account)

You can do this by running gksudo nautilus and finding the files that bring up the error.

Start with /usr/share/applications/dvdrip.desktop

And go through them one at a time, until they are all fixed with the proper permissions. Just right-click on the file and select the permissions tab, and make sure they are readable.

---

### Post by Swiss on 2006-02-27
Thanks! That worked... :)

---

