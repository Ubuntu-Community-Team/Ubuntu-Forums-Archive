---
title: "Problem with SMEG"
date: 2005-09-24
forum: Desktop Environments
---

### Post by Cloud[01] on 2005-09-24
All right all was doing fine until I decided to put America's Army in the Menu.

I think because of the " ' ".

Anyway, I tried removing and re-installing it but nothing, it still gives me this error:

```
cloud@ubucloud:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 27, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 41, in parse
    self.menu = parse()
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
    elif menuentry.DesktopFileID == 'America's Army.desktop':
                                             ^
SyntaxError: invalid syntax
```

Any help would be apreciated :)

Thank you very much!

ciop ciop

---

### Post by siggisiggibangbang on 2005-09-24
You can try to purge the package with **sudo apt-get remove --purge smeg**.  I've never used smeg myself, but these errors are familiar to me.  
Try to escape the "'" with a backslash when writing the name into the editor.  
For example "America\'s Army".  

regards
siggi

---

### Post by Cloud[01] on 2005-09-24
Tried that but still doesn't work after:

```

sudo apt-get remove --purge smeg
sudo apt-get install smeg

```

:(

Any suggestion?

As for the Future I'll put just Americas Army :P

ciop ciop

---

### Post by cwaldbieser on 2005-09-24
[QUOTE='Cloud[01]']Tried that but still doesn't work after:

```

sudo apt-get remove --purge smeg
sudo apt-get install smeg

```

:(

Any suggestion?

As for the Future I'll put just Americas Army :P

ciop ciop[/QUOTE]

Not sure what version you are using-- I heard of this bug before, so it is possible it was corrected in a later version.  You probably just have to remove the apostrophe from the config file where your menu entries are stored.  I tried downloading the souce to find out where that config file is, but I could only seem to find the binaries.  Maybe if you ask in the SMEG sub-forum, someone could tell you where the config is, and whether or not the bug has been fixed in a newer version.

---

