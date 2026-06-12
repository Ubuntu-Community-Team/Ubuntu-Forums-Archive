---
title: "gvfs: how to unset/remove attribute?"
date: 2010-07-02
forum: Desktop Environments
---

### Post by geod on 2010-07-02
How do I unset/remove attribute metadata::custom-icon?

I've set a custom icon to a folder via terminal eg:
gvfs-set-attribute myfolder metadata::custom-icon 
file:///usr/share/pixmaps/gnome-spider.png 

but I want to be able to undo this with a terminal command.

---

### Post by geod on 2010-07-05
bump

---

### Post by Dart00 on 2010-08-18
BUMP

Been wondering this too....

---

### Post by nicegiving on 2010-09-07
> **geod said:**
> How do I unset/remove attribute metadata::custom-icon?

I've set a custom icon to a folder via terminal eg:
gvfs-set-attribute myfolder metadata::custom-icon 
file:///usr/share/pixmaps/gnome-spider.png 

but I want to be able to undo this with a terminal command.

I find the solution on "http://old.nabble.com/How-do-I-change-a-folder-icon-from-a-script--td25832597.html":
gvfs-set-attribute myfolder -t unset metadata::custom-icon

But I have another question, my system is Ubuntu 9.04 desktop edition, there is no command gvfs-set-attribute on it, why?

---

