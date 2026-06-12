---
title: "Drives mounted by default. How to turn off?"
date: 2007-10-25
forum: Desktop Environments
---

### Post by Weezer on 2007-10-25
I apologize, as this doesn't properly fit the forum section, but the annoyance does stem from me preferring a clean desktop:


Whenever I log into Ubuntu, my other partitions are always mounted by default. If I try to delete them, it says I need root access, but I can unmount them by "sudo umount blahblah". How do I make it so that they are not mounted by default, as I like my desktop to be clean and void. 

Many thanks.

---

### Post by raeb on 2007-10-25
Well, I'm pretty sure you DO want them mounted automatically, you just don't want their icons on the desktop.  Type this into a terminal:

gconf-editor

Brows through apps -> nautilus -> desktop.  Uncheck the box for volumes visible.  Should help.

---

### Post by Weezer on 2007-10-25
Cool; thanks!

---

