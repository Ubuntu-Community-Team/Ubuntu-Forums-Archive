---
title: "Folders Under &quot;Places&quot; Not Themed?"
date: 2008-10-30
forum: Desktop Environments
---

### Post by DeadSuperHero on 2008-10-30
Here's a weird bug, I'm not really sure how to explain it.

If you look at the folders in the file manager on the side, they all have the same wonderful look to them.

However, under the "Places" menu, they're the gray old-school GNOME folders.

Why is this? Also, what can I do to fix it?

On a separate note, is it possible to edit the "Places" folders to have nifty little icons related to what's inside the folder (as in, say, a filmstrip on a folder for movies and such?)

---

### Post by tuxxy on 2008-10-31
[https://bugs.launchpad.net/ubuntu/+source/tango-icon-theme/+bug/284169](https://bugs.launchpad.net/ubuntu/+source/tango-icon-theme/+bug/284169)

---

### Post by infinito on 2008-10-31
You should go to your icon theme folder, and do this:

$ cd ~/.themes/your_theme/scalable/places/
$ ln -s folder.svg inode-directory.svg


New icon-naming-specs have this special folder (inode-directory.svg) but most of custom themes (and some officials, like Tango or Tangerine) hasn't updated yet.

---

### Post by le singe on 2008-11-08
> **Mr. Psychopath said:**
> 
On a separate note, is it possible to edit the "Places" folders to have nifty little icons related to what's inside the folder (as in, say, a filmstrip on a folder for movies and such?)

In the nautilus file browser, if you right-click on a folder and go to properties, under the emblems tab you can choose an icon that will attach to the folder, and you can choose amongst photos, pictures, documents, multimedia, etc.

And for the person who replied with the command-line fix... does this have to be done for every icon theme, or every time you change the icons, or does it stick across the board?

---

