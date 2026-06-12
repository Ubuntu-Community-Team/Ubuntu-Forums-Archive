---
title: "Add/Remove programs does not launch"
date: 2006-07-28
forum: Desktop Environments
---

### Post by marco999 on 2006-07-28
I am using Dapper 6.06. When I open Applications -> Add/remove... The window appears for the application but when the program is "Reading list of Available Applications" it suddenly quits.

When i try to run it (/usr/bin/gksudo /usr/bin/gnome-app-install) from the Terminal I get the following:

Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files)

** (gnome-app-install:8427): WARNING **: return value of custom widget handler was not a GtkWidget
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 171, in __init__
    self.updateCache()
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 667, in updateCache
    progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 124, in __init__
    self.refresh(progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 269, in refresh
    menu = xdg.Menu.parse(os.path.join(self.menudir, "applications.menu"))
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
    __parse(doc, filename, tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
    __parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
    __parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 586, in __parse
    __parseDefaultMergeDirs(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 762, in __parseDefaultMergeDirs
    __parseMergeDir(os.path.join(dir, "menus", basename + "-merged"), child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 755, in __parseMergeDir
    __mergeFile(os.path.join(value, item), child, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 791, in __mergeFile
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


Could you please tell me what to do to get this program working?

If it would help I also have the same problem with Alcarte.

Thanks 
Marco999

---

