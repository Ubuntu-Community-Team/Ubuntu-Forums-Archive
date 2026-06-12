---
title: "How to fix missing menu item?"
date: 2009-01-30
forum: Desktop Environments
---

### Post by John Wiersba on 2009-01-30
I just installed a bunch of applications via Add/Remove and rebooted.  Now the game Enigma, which I had previously installed, is missing from Applications -> Games and also from System -> Preferences -> Main Menu.  However, it shows up as being installed in Add/Remove and I can play it by starting it from the command line.  

How can I recover it back into my menus and also the Main Menu application?  Is there a way to get Gnome to regenerate the items in its menu?

---

### Post by Shazaam on 2009-01-31
System>Preferences>Main Menu, right side, "New Item".

---

### Post by John Wiersba on 2009-01-31
Thanks, Shazaam.  I will use this method if I can't get anything else to work.  But I would like to regenerate all my menus rather than create my own menu item, if possible.

I've tried removing applications.menu and settings.menu from ~/.config/menus, but that hasn't fixed it.  I also tried removing Enigma and reinstalling it, again without success.

I also wonder what other items are not showing up in the menus that should (did I just notice the tip of the iceberg?).

---

### Post by John Wiersba on 2009-02-01
Now, I'm not sure if this menu item (Enigma) ever showed up.  I found that /usr/share/applications/enigma.desktop had a "TryExec" line in it that was preventing it from showing in the menu.  When I comment out that line, it shows up in the menu.

---

