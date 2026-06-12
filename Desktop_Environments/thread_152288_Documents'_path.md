---
title: "Documents' path"
date: 2006-03-29
forum: Desktop Environments
---

### Post by hove99 on 2006-03-29
Hi

When I add a folder called "Documents" to my home directory and check the box "documents_icon_visible" in the gconf-editor, a folder Called Documents appears on my desktop as well as in Nautilus.

Is it possible to change the path of the "Documents" folder on the desktop (like in windows), so it does not have to be ~/Documents?

Cheers

---

### Post by Ramses de Norre on 2006-03-29
I guess the easiest way is just creating a symlink then..
```
ln -s ~/Documents ~/Desktop/Documents
``` (but change the paths ;))

---

### Post by hove99 on 2006-03-29
Hi, and thanks for the answer :-)

A symlink creates a link to my (real) documents folder e.g. "/media/somewhere/documents" and places a shortcut on the desktop. But I was looking to change the path of Gnome's standard folder called "Documents" generated on the desktop by setting "documents_icon_visible" to true in gconf-editor. The folder (not a symlink) appears only if the folder "~/Documents" written as shown is created. 

Anyway to change the Gnome standard path of "Documents" so the non-symlink shortcut appears only e.g. if /media/somewhere/documents exists?

Cheers

---

### Post by hove99 on 2006-03-30
I worked around the problem by making a symbolic link to the folder, in which my documents are:

cd ~/
ln -s /media/somewhere/documents Documents

Having enabled gconf-editor to show the Documents folder on the desktop, the Documents link (gnome standard) goes to /media/somewhere/documents

---

