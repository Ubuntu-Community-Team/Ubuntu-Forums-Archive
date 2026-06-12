---
title: "Location of desktop panel files"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Charles Hand on 2006-09-13
I assume the contents and configuration of gnome panels on the desktop are described in a text file somewhere. Where are those files?

---

### Post by CatKiller on 2006-09-14
There's information about the panels generally in gconf (Configuration Editor) at apps/panel/, which is a different way of accessing XML information from somewhere in your Home folder - not sure exactly where, I normally use gconf. It's probably ~/.gconf/apps/panel/ though.

There's also information about launchers that you've got on your panel as .desktop files in ~/.gnome2/panel2.d/default/launchers/

It's all a bit messy to fidddle with the text files though, IMO. What is it that you're trying to do that isn't easier using the mouse?

---

### Post by Charles Hand on 2006-09-16
Copy a launcher and modify it slightly.

---

### Post by CatKiller on 2006-09-17
> **Charles Hand said:**
> Copy a launcher and modify it slightly.

So did you find them?

---

### Post by Charles Hand on 2006-09-17
In .gnome2/panel2.d/default/launchers, each launcher is contained in a file whose name has three parts: the name of a stooge, or "bar" or "hammer" or some such, ten-character hex number (a digest of some kind or a key perhaps?), and a .desktop extension. e.g.: moe-000aab29e1.desktop. Inside the file are plain text property/value pairs. I'll try copying one of them and naming it xxx.desktop.

---

### Post by Charles Hand on 2006-09-17
No dice. The file was ignored.

---

### Post by CatKiller on 2006-09-18
What I've usually done to modify them is to copy them to the desktop before editing them, and then putting them on the panel when I know they work. Launchers on the desktop would just be some command, but wouldn't the panel require some kind of geometry information elsewhere, so that it knew where to display it? I don't really know that much about the panel or .desktop files, but I have managed to create a few custom launchers, so I know that it's possible.

The name doesn't matter, since it's the internal one that gets displayed. Whenever I've dragged a launcher onto the panel, the launcher on the desktop has remained, and a new one with a unique random name gets generated in that folder.

---

