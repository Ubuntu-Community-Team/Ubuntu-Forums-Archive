---
title: "Application Menu Editor wont start"
date: 2006-04-22
forum: Desktop Environments
---

### Post by amunimanghi on 2006-04-22
hi

i downloaded a program called showimg. I expected it to be under the graphics tab under the menu but it isnt. I wanted to add it using the application menu editor but that wont start. its been like this for a while but i never really used it. only to add a 'python' selection under programming. Does anyone know how i may fix this?

---

### Post by Qrk on 2006-04-22
Try starting it from a terminal and paste the error messages it spits out here. 

```
smeg
```

Edit: So not everyone uses Dapper

---

### Post by Ramses de Norre on 2006-04-22
The command is smeg.

---

### Post by amunimanghi on 2006-04-22
okay this is what it shows.

```
******@ubuntu:~$ smeg
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
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
    __parse(doc, filename, tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 575, in __parse
    __parseMergeFile("applications.menu", child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 742, in __parseMergeFile
    __mergeFile(os.path.join(p,rel_file),child,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 785, in __mergeFile
    __parse(child,filename,parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 586, in __parse
    __parseDefaultMergeDirs(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 762, in __parseDefaultMergeDirs
    __parseMergeDir(os.path.join(dir, "menus", basename + "-merged"), child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 755, in __parseMergeDir
    __mergeFile(os.path.join(value, item), child, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 785, in __mergeFile
    __parse(child,filename,parent)
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
    elif :
         ^
SyntaxError: invalid syntax
******@ubuntu:~$

```

---

### Post by apolyak on 2006-04-22
thanks to magnusbb, you can find the fix here
[http://ubuntuforums.org/showthread.php?t=142868&highlight=alacarte](http://ubuntuforums.org/showthread.php?t=142868&highlight=alacarte)

---

