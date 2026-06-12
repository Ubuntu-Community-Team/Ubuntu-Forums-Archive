---
title: "Alacarte has disappeared?!"
date: 2006-11-27
forum: Desktop Environments
---

### Post by tigershark on 2006-11-27
Hi

I've accidentally removed the Alacarte menu editor from my startmenu... :???: 

How do I do to take that back, it must be some conf-file somewhere?!

---

### Post by ButteBlues on 2006-11-27
Just run "alacarte" in the Alt+F2 run dialog and then manually re-add the link.

It's relatively easy.

---

### Post by tigershark on 2006-11-27
But then the new problem is: I have turned of all the keyboardshortcuts.... :???: 

There must be a conf-file for alacarte somewhere?...

Or can you start alacarte without an x-server?

---

### Post by FastZ on 2006-11-27
System > Preferences > Menu layout
 
Unless that is just a menu option that was put in for Edgy.

---

### Post by tigershark on 2006-11-27
Can't find anything useful there.

The problem is that I unchecked every checkbox  from the startmenu using Alacarte menu editor and then I closed it.

And now there is no way to get it back...:(

---

### Post by bapoumba on 2006-11-27
Just run **alacarte** from a terminal ;)

---

### Post by CatKiller on 2006-11-27
It doesn't really matter that I can't think of a reason why you'd want to disable all the ways of running anything at all, but does right-clicking on the menu still work?

Failing that, the user menu configuration is stored in the **~/.config/menus/applications.menu** file. You can edit that - if you have to - with **nano** from the command line. You can get to the command line - if you have to - with **Ctrl-Alt-F2**. This will take you to the second of your virtual consoles. **Alt-F7** will take you back to your graphical login.

**killall gnome-panel** will refresh the menu - if you have to.

---

