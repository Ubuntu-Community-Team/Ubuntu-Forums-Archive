---
title: "Nautilus bug"
date: 2008-11-09
forum: Desktop Environments
---

### Post by dbutler1986 on 2008-11-09
When I double-click a folder location on the desktop, all the icons disappear for several seconds while the cursor switches to the 'waiting' cursor, and then the file browser never opens. If I manually run 'nautilus' from a terminal the folder opens, but when I double-click any item inside the file browser window disappears along with the desktop icons. The icons come back but the file browser doesn't, and whatever I double-clicked didn't open (be it video or audio or text or whatever). How can I find out what's wrong?

---

### Post by jpeddicord on 2008-11-09
Sounds like nautilus is crashing. You can grab a crash dump to report a bug about it by following the directions on "How to enable apport" on [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport). Restart your system after doing those instructions, and open a folder to do what you described. A few moments later, Apport should pop up with a report to automatically send in.

---

