---
title: "Ugh... smeg (Applications Menu Editor) problems..."
date: 2006-02-27
forum: Desktop Environments
---

### Post by WackToMack on 2006-02-27
Hello everyone!  For some strange reason, Applications Menu Editor stopped working.  When I click on the button to start it, it just hangs and closes.  These are the errors I get when using this code:

```
smeg
```

in the Terminal.

> wacktomack@Linux:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 559, in main
    smeg.run()
  File "/usr/bin/smeg", line 553, in run
    self.getMenus()
  File "/usr/bin/smeg", line 142, in getMenus
    self.handler.loadMenus()
  File "/usr/lib/smeg/MenuHandler.py", line 163, in loadMenus
    self.depths[depth] = self.renderer.addMenu(entry, self.depths, depth)
  File "/usr/bin/smeg", line 151, in addMenu
    pixbuf = self.getIcon(menu)
  File "/usr/bin/smeg", line 74, in getIcon
    path = self.handler.getIconPath(entry, size)
  File "/usr/lib/smeg/MenuHandler.py", line 119, in getIconPath
    path = xdg.IconTheme.getIconPath(icon, size, self.theme)
  File "/usr/lib/python2.4/site-packages/xdg/IconTheme.py", line 275, in getIconPath
    if iconname + "." + extension in values[0]:
UnicodeDecodeError: 'utf8' codec can't decode byte 0x82 in position 24: unexpected code byte


Any ideas on how to fix this?  Thanks in advance! :D

---

### Post by WackToMack on 2006-02-28
BUMP!!!  Anyone??? :confused:

---

### Post by remin8 on 2006-03-03
One this you can do is run: 
```
sudo smeg
```
This worked for me... one you get into the menu editor edit the command to sudo smeg as well. Hope this helps.

---

### Post by ins on 2006-03-06
Not sure if this will help, but it cured my menu editor problems:
```

sudo chown user_name /usr/share/applications/*

```

I was having a similar problem right after using Automatix to install some goodies; and when running smeg from the terminal it gave me a permissions error message... hence the change of ownership of the .desktop files within the applications directory.

---

### Post by jamper on 2006-03-08
@ins it worked for me
thanks

---

