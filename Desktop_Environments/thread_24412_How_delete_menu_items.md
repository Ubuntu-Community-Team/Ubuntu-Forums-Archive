---
title: "How delete menu items?"
date: 2005-04-06
forum: Desktop Environments
---

### Post by lagagnon on 2005-04-06
I have just installed Hoary. Another almost exact same machine has Warty. Differences and annoyances (how solve):

1) how do I delete a menu item? On Warty I just right clicked and chose "Delete" .
2) the mouse behaves differently on the menu. I have to hold down the left button to navigate or the menu disappears!! Not in Warty! How can I change this behaviour?

---

### Post by skoal on 2005-04-06
[QUOTE=lagagnon]1) how do I delete a menu item? On Warty I just right clicked and chose "Delete" .[/QUOTE]
After upgrading to hoary, I had multiple 'beep-media-player' desktop entries.  Of course, there is no default menu editor in Gnome 2.10 (but you can download some external GUIs for that, see the wiki).

All your menu entries are .desktop files.  With Gnome 2.10, I believe they should be in '/usr/share/applications'.  If you want to add/delete a menu entry, do it there.

For some reason, I had some legacy .desktop file (from Warty I believe) in '/usr/share/gnome/apps' (subdirectories).  I had to delete a duplicate in one of these subs.

[QUOTE=lagagnon]
2) the mouse behaves differently on the menu. I have to hold down the left button to navigate or the menu disappears!! Not in Warty! How can I change this behaviour?[/QUOTE]
It doesn't do that for me in hoary.  I don't know how to change that feature but I assume it's something related to a theme or a system configuration option.

---

