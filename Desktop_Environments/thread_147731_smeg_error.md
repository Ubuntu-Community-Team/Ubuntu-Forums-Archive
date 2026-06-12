---
title: "smeg error"
date: 2006-03-20
forum: Desktop Environments
---

### Post by emperor on 2006-03-20
smeg is failing to run due to the following error. 
Any suggestions on how to determine what is apparently missing?

emperor@realm:~$ sudo smeg
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

---

### Post by emperor on 2006-03-21
I found the fix here:
[http://ubuntuforums.org/showthread.php?t=142868&highlight=alacarte](http://ubuntuforums.org/showthread.php?t=142868&highlight=alacarte)

---

