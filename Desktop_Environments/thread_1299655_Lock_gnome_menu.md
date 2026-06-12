---
title: "Lock gnome menu"
date: 2009-10-24
forum: Desktop Environments
---

### Post by oddchild on 2009-10-24
Hi All,


I have installed Ubuntu recently on a childrens computer lab. I need a way to prevent kids from being able to change the menu / desktop. Is there any way that I can restrict this?


Thanks

Johnny

---

### Post by gitboxgreg on 2009-10-27
ubuntu tweak [http://www.getdeb.net/release.php?id=4775](http://www.getdeb.net/release.php?id=4775) has a lock down all gnome-panels option.

---

### Post by mcduck on 2009-10-27
> **gitboxgreg said:**
> ubuntu tweak [http://www.getdeb.net/release.php?id=4775](http://www.getdeb.net/release.php?id=4775) has a lock down all gnome-panels option.

..and the same option is available directly in gconf-editor, without having to install any extra software for it.

Just press Alt-F2 and run "gconf-editor", browse to apps/panel/global and enable the "locked_down"-key.

Gnome also has couple of graphical tools for configuring & locking down the desktop for different users/groups. Pessulus is for locking down the desktop, and Sabayon is for configuring the settings for different users & groups. Although these might be a bit overkill if you only need to manage one user account...

---

### Post by oddchild on 2010-01-21
Thanks guys... That will save me a lot of trips to and redo the panel each time. :)

---

