---
title: "SuperKaramba"
date: 2006-02-23
forum: Desktop Environments
---

### Post by tadashi on 2006-02-23
How do you know if this is installed?  I first installed it using a package manager.  However, I could not tell if it was installed.  It looked like my regular old KDE.  Was I suppose to run a file?

So I uninstalled it and installed it from a source file from their web site.  The ./configure said good configure go make.  Then the make file ended with no errors, and make installed ended with no errors that I could see.  I rebooted and now get:

You must use XOrg >= 6.8 for translucency and shadow to work.  Additionally you need to add a new section to your X config file:...

I have XOrg 6.8.2 installed is there something else I need and where is this X config file?

---

### Post by cwaldbieser on 2006-02-23
[QUOTE=tadashi]How do you know if this is installed?  I first installed it using a package manager.  However, I could not tell if it was installed.  It looked like my regular old KDE.  Was I suppose to run a file?

So I uninstalled it and installed it from a source file from their web site.  The ./configure said good configure go make.  Then the make file ended with no errors, and make installed ended with no errors that I could see.  I rebooted and now get:

You must use XOrg >= 6.8 for translucency and shadow to work.  Additionally you need to add a new section to your X config file:...

I have XOrg 6.8.2 installed is there something else I need and where is this X config file?[/QUOTE]

You can just install it from the package manager and run it with
```

$ superkaramba

```
It should put an icon that looks like a little bomb in your system tray.  If you click on the icon, you get a dialog that lets you load superkaramba apps.

---

### Post by f1dave on 2006-02-24
Afaik in Breezy it is installed by default.

---

### Post by tadashi on 2006-02-24
Thanks that worked.  I had to run it in the command line.  My session saver brings it up for me now.  I am surprised there was no icon for it installed in the menus (or if there is I have not found it).

---

### Post by gingermark on 2006-02-24
It's in the 'Utilities' part of the menu on my system. You could always edit your menu and add an entry for it.... It should have added itself though.

---

