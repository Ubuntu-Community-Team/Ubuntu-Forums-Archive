---
title: "Merging Applications and Computer Menu"
date: 2005-02-02
forum: Desktop Environments
---

### Post by lmunro on 2005-02-02
I'd like to maximise my available panel space by merging the Applications and Computer menus under a simple foot icon (somewhat like the Main menu). 
How would I do that? 
I know how to add items to already existing menus but I can't seem to find a way to build a custom menu... 
Does anyone know?

---

### Post by valadil on 2005-02-02
Right click on the panel and add a component to it.  Add a main menu.  Then delete the previous menu.  Gnome-panel has two similar objects, main menu and menu bar.  The menu bar is whats used by default.

As far as managing your menus goes the way to do it is with the debian menu program.
apt-get install menu
Then read up on its manual.  If you manage your menus with your wm you will eventually use all your menus when the deiban menu overwrites them.

---

