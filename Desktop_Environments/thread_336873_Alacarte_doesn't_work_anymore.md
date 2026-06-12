---
title: "Alacarte doesn't work anymore"
date: 2007-01-12
forum: Desktop Environments
---

### Post by flatko on 2007-01-12
Please help.
Alacarte stopped working for unknown reason... It just doesn't start and shows a message instead: alacarte stopped.  I tried opening it in the terminal, but it stops without writing anything in the command line... It just stops. ](*,)

---

### Post by tweedledee on 2007-01-13
> **flatko said:**
> Please help.
Alacarte stopped working for unknown reason... It just doesn't start and shows a message instead: alacarte stopped.  I tried opening it in the terminal, but it stops without writing anything in the command line... It just stops. ](*,)

Try reinstalling (via synaptic)?  Or in the event it is a .desktop file that is corrupt and crashing it, try copying everything from /usr/share/applications to another location and emptying that folder, then adding back one at a time if that works.  Last, you could flush the alacarte settings, although I don't know where those are.

---

### Post by gregster on 2007-01-16
Don't know if this helps but same here.
If I launch from the Gnome Control Center I get no indication that anything is happening.
When launched from terminal I get this:
bash: /usr/bin/alacarte: python: bad interpreter: No such file or directory

However, when I run the full path to alacarte:
$ /usr/bin/alacarte
It launches.

I'm running Herd2

---

### Post by acm79 on 2007-01-17
I've got the same problem, don't know what to do, when I put *alacarte* into console you can see....

(alacarte:6037): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(alacarte:6037): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(alacarte:6037): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed
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
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 856, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 859, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1036, in __addFiles
    self.__addFiles(dir, os.path.join(subdir,item), prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1028, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/posixpath.py", line 65, in join
    path += '/' + b
UnicodeDecodeError: 'utf8' codec can't decode byte 0xb5 in position 1: unexpected code byte

---

### Post by tweedledee on 2007-01-17
> **gregster said:**
> Don't know if this helps but same here.
If I launch from the Gnome Control Center I get no indication that anything is happening.
When launched from terminal I get this:
bash: /usr/bin/alacarte: python: bad interpreter: No such file or directory

However, when I run the full path to alacarte:
$ /usr/bin/alacarte
It launches.

I'm running Herd2

This sounds like a path problem with python, not necessarily an alacarte problem.  If Fiesty is switching over from python 2.4 to python 2.5 but hasn't updated some link, that may explain it.  You should file a bug report with the above information.

---

### Post by tweedledee on 2007-01-17
> **acm79 said:**
> I've got the same problem, don't know what to do, when I put *alacarte* into console you can see....

I can't actually walk back through that trace, because Alacarte has apparently changed significantly between Dapper and Edgy.  However, the error looks to me like it is choking on unexpected character, presumably in a .desktop file (unless one of the alacarte files itself is corrupt).  If reinstalling doesn't work, I suggest you try identifying which .desktop it is, in either /usr/share/applications or ~/.local/share/applications by moving the *.desktop files elsewhere and seeing if alacarte loads; if it does, gradually return them to see which is causing the problem.  If this approach doesn't work, file a bug report.  If it does, report back so others can use the solution.

---

### Post by acm79 on 2007-01-17
tweedledee, thank you so much! i moved wine folder from ~/.local/share/applications and alacarte launches :) so next time back, back forth and forth... ;)

---

