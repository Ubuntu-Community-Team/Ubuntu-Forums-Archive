---
title: "root"
date: 2009-10-17
forum: Desktop Environments
---

### Post by akross6966 on 2009-10-17
First off, i know this isn't windows and that this enviroment is more secure.  I think it's awesome.  I love the linux community, but not being able to figure some things out kind of aggrivates the crap right out of me.  Anyway, i am trying to copy, rename, and do some administrative stuff in gnome (e.g. copy a folder to the www folder and rename a file once i get it in there).  I'm not command-line literate which is why gnome is installed.  I can't do squat through the gui.  Would someone please show grace upon me and show me how to give myself root privalages long enought to do the admin tasks i need to do in the gui then log myself?  I will admit that I am used to the Windowz server enviroment, but I am wanting to support the linux community, and after reading about samba+zimbra to take the place of AD+exchange, i am trying to learn this new world.  Thanks in advance.

---

### Post by DGortze380 on 2009-10-17
alt+f2

gksu nautilus

If you delete large files this way, remember to empty root's trash (/root/.trash)

---

### Post by 3rdalbum on 2009-10-18
Install the "nautilus-gksu" package. Log out, and log back in again. Now whenever you need to open a folder or file as root, just right-click on it and choose "Open as Administrator".

To copy files across as root, open the destination folder as root using this method, and then you'll be able to copy, rename and move.

---

### Post by &#21315;&#23547;cc on 2009-10-18
It works. Thanks!

---

### Post by akross6966 on 2009-10-18
> **3rdalbum said:**
> Install the "nautilus-gksu" package. Log out, and log back in again. Now whenever you need to open a folder or file as root, just right-click on it and choose "Open as Administrator".

To copy files across as root, open the destination folder as root using this method, and then you'll be able to copy, rename and move.


You guyz are the bomb.  Thanks for the help.  I will do that.

---

