---
title: "Is it possible to view shortcuts only in some activities?"
date: 2020-10-18
forum: Desktop Environments
---

### Post by phileconte on 2020-10-18
Hi,
is it possible to display a shortcut only on a particular desktop  dedicated to an activity? When I create a desktop shortcut pointing to  a folder, it is displayed on all the activities. By right-click on the  shortcut icon, there is an activity menu but it is ineffective. Could it be possible to modify the [FONT=monospace][COLOR=#000000]plasma-org.kde.plasma.desktop-appl[/COLOR]
etsrc in order to do that ?
[/FONT]
Any help would be appreciated, thanks!

---

### Post by TheFu on 2020-10-18
What is a shortcut?  Do you mean  a symbolic link or something else?
Symlinks are file system objects.  There's a wkipedia article if more info is needed.

---

### Post by phileconte on 2020-10-18
Thanks,
I mean probably a Symlink (an icon on the desktop which open a folder). I'll read the xman and if needed, the wikipedia

---

### Post by TheFu on 2020-10-18
I doubt the manpage for **ln** will be too useful. **ln -s** is the way to create symlinks.

.desktop files are completely different. I don't use those. Sorry.

---

### Post by phileconte on 2020-10-18
you're welcome, 
anyway thanks to have tried

---

