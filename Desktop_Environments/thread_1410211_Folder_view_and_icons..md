---
title: "Folder view and icons."
date: 2010-02-18
forum: Desktop Environments
---

### Post by dE_logics on 2010-02-18
I'm trying the K desktop environment and I realized why many people stick to xfce and gnome. First there's the command line, and then there's KDE.

In the panels I want a list of commands (e.g. gksu kwrite /etc/fstab, gksu dolphin /etc/init.d etc...) to be opened on clicking it (like what's there is xfce).

This can be done by making custom menu entries in kick-start/lancelot and dragging the whole menu to the panel. However, the icon of this dragged item is a "?"...and I did not find any ways to change it. I have many such menus and all having the same icon makes it confusing!

If possible, is there any other way to do the same such that I can change the icon?

Here is a screenshot of the question marks - 

[IMG]http://img11.imageshack.us/img11/3605/snapshot7x.png[/IMG]

---

### Post by Zorael on 2010-02-19
There is no *easy* way to do it, but there *is* a way to get it right. Dragging stuff from the menu doesn't work well.

You want to create a custom launcher (.desktop file) and save it someplace, then drag it to your panel. Note that if you delete the launcher file, the panel icon will also disappear. So save it someplace out of sight and out of mind, like in **~/.misc** or whatnot.

In Dolphin, in Konqueror or in a folder view widget/activity, right click empty space and pick Create New -> Link to Application. Set it up as you please.

A notable inconsistency is that the mouseover tooltip will display the launcher's name and comment when mouseovering the file, but the launcher's name and description when mouseovering it when it's in a panel.

---

