---
title: "Trashcan problem"
date: 2006-07-09
forum: Desktop Environments
---

### Post by linuxfan128 on 2006-07-09
I removed the trashcan from the bottom right hand corner of the gnome panel. I cant figure out how to put it back i tried moving the workspace selector to the left but the move option grayed out. Can i restore default somehow? i also want to know how i can put a trashcan on my desktop.

---

### Post by Wolki on 2006-07-09
> **linuxfan128 said:**
> I removed the trashcan from the bottom right hand corner of the gnome panel. I cant figure out how to put it back i tried moving the workspace selector to the left but the move option grayed out.

Adding it: right-click on the panel -> add to panel -> Trash applet.
Putting it back to it's old space: the other applets are locked. Right-Click the ones that are in the way and select unlock; then middleclick-hold the trash can applett and drag it to the space where you want it to go.

> Can i restore default somehow? i also want to know how i can put a trashcan on my desktop.

alt-f2 -> gconf-editor -> /apps/nautilus/desktop/ -> check trash_icon_visible

---

### Post by Nonno Bassotto on 2006-07-09
Did you check if the workspace selector is locked? When you right click on an item on the panel, you have the option to lock it, so you don't move it accidentally, and other items don't push it.

---

### Post by linuxfan128 on 2006-07-09
Thanks allot it was locked. Problem solved.

---

