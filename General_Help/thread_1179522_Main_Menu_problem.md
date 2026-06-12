---
title: "Main Menu problem"
date: 2009-06-05
forum: General Help
---

### Post by WildeBeest on 2009-06-05
Jaunty

When I try to select to System->Preferences-Main Menu, nothing happens.

Does anyone else have this problem?

How do I fix it?

---

### Post by CatKiller on 2009-06-05
What happens if you run alacarte in a Terminal?

---

### Post by WildeBeest on 2009-06-05
```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/wildebeest/.config/menus/applications.menu'

```

I changed the permissions on the .config/menus folder.
Now it works.

Thanks

---

