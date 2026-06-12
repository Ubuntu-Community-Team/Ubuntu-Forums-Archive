---
title: "Fluxbox Problems."
date: 2005-08-27
forum: Desktop Environments
---

### Post by Sheytan on 2005-08-27
OK i have installed fluxbox and it's config apps like fluxconf, fluxmenu etc

And the only thing i get on the menu is xterm, exit and onother menu entry.
I have tried to use this command "fluxbox-generate_menu" but it doesn't work,
i get this answer "fluxbox-generate_menu: command not found"

I have tried fluxmenu but when i try to add some new entrys i get this in the terminal.

"(fluxmenu:8516): Gtk-CRITICAL **: gtk_tree_store_append: assertion `VALID_ITER ( parent, tree_store)' failed

(fluxmenu:8516): Gtk-CRITICAL **: gtk_tree_store_append: assertion `VALID_ITER ( parent, tree_store)' failed

(fluxmenu:8516): Gtk-CRITICAL **: gtk_tree_store_set: assertion `VALID_ITER (ite r, tree_store)' failed

(fluxmenu:8516): Gtk-CRITICAL **: gtk_tree_store_set: assertion `VALID_ITER (ite r, tree_store)' failed"

---

### Post by dbcoder on 2005-08-27
Well, I would recommend compiling fluxbox, it's not hard to do and I can tell you how to do it if you would like.

Compiling it will be the best option because when it configures I believe it locates everthing on your system instead of using default locations.  It also generates a nice menu for you too.

---

### Post by dbcoder on 2005-08-27
Well, I would recommend compiling fluxbox, it's not hard to do and I can tell you how to do it if you would like.

Compiling it will be the best option because when it configures I believe it locates everthing on your system instead of using default locations. It also generates a nice menu for you too.

---

### Post by baked on 2006-07-09
Hey, 

Right now I am having the same problems as you are experiencing.  It was all working and I added 'xterm' as an exec inside of the shells menu and it all went away and if I run fluxmenu now I cant add anything and am getting the same error as above.  If anyone knows how to fix the problem please let me know.  I'll post it up if I find a fix.

Thanks,

Tommy.

---

### Post by yabbadabbadont on 2006-07-09
Please post the contents of your ~/.fluxbox/menu file.

---

### Post by yosef on 2006-07-10
> **dbcoder said:**
> Well, I would recommend compiling fluxbox, it's not hard to do and I can tell you how to do it if you would like.

Compiling it will be the best option because when it configures I believe it locates everthing on your system instead of using default locations. It also generates a nice menu for you too.

Well, I would appreciate you telling us how to compile it if it isn't hard... I synapticed fluxbox and have no menu at all and the fluxbox-generate_menu doesn't work.

---

### Post by yabbadabbadont on 2006-07-10
If you installed Fluxbox using synaptic, then you should be able to run:

sudo update-menus

Then the default menu used by the Ubuntu fluxbox package should pick up most apps that have been installed through synapic or apt-get.

If not, post your ~/.fluxbox/menu file so that we can see what has been created for you.  Also post your ~/.fluxobx/init file, since it specifies which menu file is to be used.

---

