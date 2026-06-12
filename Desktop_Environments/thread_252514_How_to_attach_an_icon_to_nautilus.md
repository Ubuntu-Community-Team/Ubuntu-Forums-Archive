---
title: "How to attach an icon to nautilus"
date: 2006-09-06
forum: Desktop Environments
---

### Post by DagonX on 2006-09-06
For some reason nautilus doesn't show up in any of the menues. I would like to attach an icon to it so I can lauch it from the desktop, instead of a terminal. So how can I attach an icon to it?

Related question. I have to write several batch files to start some applications. How do I attach icons to the script files so I can start them fromthe desktop?

---

### Post by bviking on 2006-09-07
the "places" menu item launches nautilus.

---

### Post by petersjm on 2006-09-07
Open a terminal and type **gconf-editor** then hit enter. When the editor pops up, use the left-hand tree to go to Apps > Nautilus > Desktop and from there you can select "Computer_icon_visible" and that puts nautilus on your desktop.

---

### Post by crossedout on 2006-09-07
Could also right-click, add launcher, Command->nautilus.  Then choose your icon while you are there.  Although I would think petersjm has the more logical option.

-Xout

---

### Post by CatKiller on 2006-09-08
> **DagonX said:**
> For some reason nautilus doesn't show up in any of the menues.

Right-click on the menu bar and select "Edit Menus". Go to Accessories and put a tick in the box next to File Browser.

Then Applications -> Accessories -> File Browser will launch Nautilus.

---

