---
title: "Add menu item in alacart - 'new entry' button missing"
date: 2006-07-12
forum: Desktop Environments
---

### Post by immanueloffice on 2006-07-12
Ubuntu Dapper, AMD 64

I've been trying to add a menu item (Beagle) to my accessories menu.

1. Is there something I should do that it should show up automatically?

2. I have to run alacarte menu editor as gksudo. Is this normal?

3. Once I have alacarte running, I don't see any 'new entry' link or button that I have seen references to, so I can't seem to add a new entry.

I don't know if any of these are connected. And ideas?

Thanks!

---

### Post by immanueloffice on 2006-07-19
I have figured out how to add an item (File->New Entry) but if I run Alacarte as gksudo, it doesn't show up in my own menu.

If I run Alacarte from the command line, this is the error message I get:

(alacarte:24285): GnomeUI-CRITICAL **: gnome_icon_selection_stop_loading: assertion `gis != NULL' failed
/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py:54: GtkWarning: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
  self.tree = gtk.glade.XML(
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 26, in ?
    main()
  File "/usr/bin/alacarte", line 23, in main
    GnomeFront()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 72, in __init__
    self.loadMenus()
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 201, in loadMenus
    self.app_handler = MenuHandler('applications.menu', self.options)
  File "/usr/lib/python2.4/site-packages/Alacarte/PyXDGMenuHandler.py", line 27, in __init__
    xdg.MenuEditor.MenuEditor.__init__(
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 40, in parse
    self.menu = parse(menu)
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
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 791, in __mergeFile
    __parse(child,filename,parent)
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

[1]+  Exit 1                  alacarte

I have Python 2.4 (2.4.3-0ubuntu4) installed, and I just reinstalled it to see if that would help, but no change.

---

