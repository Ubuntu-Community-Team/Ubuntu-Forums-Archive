---
title: "Problem running alacarte as root"
date: 2012-10-04
forum: Desktop Environments
---

### Post by doktorOblivion on 2012-10-04
Getting the following error, anyone have any ideas?

```

$ sudo xfce4-panel 
[sudo] password for egriffin: 

(xfce4-panel:23028): GLib-WARNING **: (/build/buildd/glib2.0-2.32.3/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)
xfce4-panel: Failed to connect to session manager: Verbindung zur Sitzungsverwaltung fehlgeschlagen: SESSION_MANAGER environment variable not defined
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 44, in __loadMenus
    self.applications.path = os.path.join(util.getUserMenuPath(), self.applications.tree.get_menu_file())
  File "/usr/lib/python2.7/posixpath.py", line 66, in join
    if b.startswith('/'):
AttributeError: 'NoneType' object has no attribute 'startswith'
^C
(xfce4-panel:23028): xfconf-CRITICAL **: xfconf_cache_old_item_end_call: assertion `old_item->call' failed

```

My path is set to:
```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

```

and there is no PERLLIB setting.

---

### Post by rai4shu2 on 2012-10-04
Maybe use gksudo instead of sudo (although why you'd run as root...)?

---

