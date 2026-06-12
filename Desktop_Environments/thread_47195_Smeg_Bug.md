---
title: "Smeg Bug"
date: 2005-07-07
forum: Desktop Environments
---

### Post by apollo2011 on 2005-07-07
I used Smeg to add a menu entry for America's Army.  I entered it as "America's Army".  Apparently, Smeg doesn't like the apostrphe so it won't load now.  I deleted the America's Army entry from ~/.local/share/applications and it still won't load.  Apparently data about the entry is stored in a file, but the error report when loaded in the terminal is far to vague for me to tell where the file is stored.  Below is the text I get when I attempt to load Smeg.

```
$ smeg
None
Traceback (most recent call last):
  File "/usr/bin/smeg", line 559, in ?
    main()
  File "/usr/bin/smeg", line 555, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 57, in __init__
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
    elif menuentry.DesktopFileID == 'America's Army-1.desktop':
                                             ^
SyntaxError: invalid syntax
$

```

---

### Post by Ferio on 2005-07-22
Exactly the same has happened to me, this is the 3rd thread in which I post this, I hope someone has a fix for it...

 ```
None
Traceback (most recent call last):
  File "/usr/bin/smeg", line 559, in ?
	main()
  File "/usr/bin/smeg", line 555, in main
	smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
	self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 57, in __init__
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
	elif menuentry.DesktopFileID == 'Waste's Edge.desktop':
										   ^
SyntaxError: invalid syntax
```

---

### Post by Ferio on 2005-07-22
I got it; just edit your /home/your_user/.config/menu/applications.menu and delete the entry that includes the apostrophe, SMEG seems to have some problems with them :)

---

### Post by jimbob on 2005-07-23
I do not have a /home/your_user/.config directory in Hoary.   Is this a typo?

---

