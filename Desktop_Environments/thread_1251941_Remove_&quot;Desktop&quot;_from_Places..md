---
title: "Remove &quot;Desktop&quot; from Places."
date: 2009-08-28
forum: Desktop Environments
---

### Post by credobyte on 2009-08-28
As thread title says .. is there a way to remove "Desktop" from Gnome menu bookmarks ? I've already hided it from Nautilus but can't figure out, how to remove/hide it from bookmarks.

---

### Post by DaithiF on 2009-08-28
Hi, I don't think there is a 'proper' way to do this, as it seems that the Places menu is hardwired to create both a Home Folder and a Desktop item, before then appending whatever bookmarks exist.

Looking at the code though, when creating the Desktop item, there is a check for a gconf key:  DESKTOP_IS_HOME_DIR - if that exists then the Desktop menu item is not created.

I tried setting this key to true in gconf-editor:  /apps/nautilus/preferences/desktop_is_home_dir, and yes, it does cause the Desktop menu item to disappear from Places.  Not sure what other consequences it may have :) , but nothing I've noticed so far.

---

### Post by credobyte on 2009-08-28
> **DaithiF said:**
> Hi, I don't think there is a 'proper' way to do this, as it seems that the Places menu is hardwired to create both a Home Folder and a Desktop item, before then appending whatever bookmarks exist.

Looking at the code though, when creating the Desktop item, there is a check for a gconf key:  DESKTOP_IS_HOME_DIR - if that exists then the Desktop menu item is not created.

I tried setting this key to true in gconf-editor:  /apps/nautilus/preferences/desktop_is_home_dir, and yes, it does cause the Desktop menu item to disappear from Places.  Not sure what other consequences it may have :) , but nothing I've noticed so far.

Thank you! Looks like it did the trick :)

---

### Post by Hack.The.Pow. on 2010-10-25
hey guys.  So i followed what you said and it did the trick perfectly.

Only question is now all the folders that were in my home directory are now on my desktop.  (I know that is essentially what we did by changing that key)

I wanna know if theres a way to hide these folders on my desktop?(I don't mind seeing them in the file browser)  I like having a pretty blank looking desktop.

---

### Post by DaithiF on 2010-10-26
> **Hack.The.Pow. said:**
> 
I wanna know if theres a way to hide these folders on my desktop?(I don't mind seeing them in the file browser)  I like having a pretty blank looking desktop.

Not that I know of.  I also like a blank desktop, for that reason I leave that flag unset, and leave the Desktop folder empty.  Desktop still shows up in Places menu, but that doesn't bother me.

---

### Post by Zvlwab on 2011-07-26
in gconf-editor uncheck apps/nautilus/preferences/show_desktop
This causes some graphical bugs in ubuntu 11.04 though. It makes the desktop unclickable and removes all icons :)

---

