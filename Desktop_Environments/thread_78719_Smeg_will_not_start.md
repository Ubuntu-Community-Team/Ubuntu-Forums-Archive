---
title: "Smeg will not start"
date: 2005-10-18
forum: Desktop Environments
---

### Post by silux on 2005-10-18
I try to right click on the applications menu and go to edit menu... the starting application notification on the taskbar starts ...

...

and the it stops, nothing happens.

Its kind of anti-climatic.  It would be nice if gnome gave me some indication of what the heck happened but it didn't.  Anyway when you run smeg by hand on the command line this is what I get

>   File "/usr/bin/smeg", line 30, in ?
    from MenuHandler import MenuHandler
  File "/usr/lib/smeg/MenuHandler.py", line 29, in ?
    import xdg.Menu, xdg.Config, xdg.IniFile, xdg.MenuEditor, xdg.BaseDirectory
ImportError: No module named Config

[1]+  Exit 1                  smeg

Well from reading around I see some people have had similar problems because they do not have the package python-xdg installed, I however do have this package installed (.15).  Besides if it was an issue with python.xdg wouldn't it complain about the menu xdg file before config.

Any ideas?

---

### Post by Dr. Nick on 2005-10-18
try to reinstall maybe, search for smeg in synaptic and click mark for resinstallaion, also check for broken packages "Custom -> Broken" in synaptic 
Not sure why it would do this in the firest place, is this a fresh install or upgrade?

---

### Post by silux on 2005-10-19
This is an upgrade, I already tried re-installing smeg, I even did a complete uninstall and then re-insalled it.  Still no luck.

---

### Post by bluevoodoo1 on 2006-05-20
This is an old post... but

I had a similiar problem, reinstalling the "menu-xdg" package solved it. Be sure to back up your menu first. 

```
cp .config/menus/applications.menu .config/menus/applications.menu_backup
```

---

