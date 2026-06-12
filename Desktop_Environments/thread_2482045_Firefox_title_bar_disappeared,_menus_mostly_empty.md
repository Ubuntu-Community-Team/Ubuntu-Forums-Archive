---
title: "Firefox title bar disappeared, menus mostly empty"
date: 2022-12-17
forum: Desktop Environments
---

### Post by peyre on 2022-12-17
I turned on my computer last night and opened Firefox as usual, and the browser's all messed up.  The title bar is missing, and most of the menu items are blank, including--all my bookmarks are gone.  The minimize, restore, and close icons in the top left are also gone, though they outline if I hover the mouse over them (and the close button doesn't work).  It's a hell of a thing to come home to after a long day at the office.  Anyone know what to do about it?  I've tried removing and reinstalling in Synaptic, but it just goes back to the same behavior.  Anyone know how to fix this?  (I'm running Xubuntu 22.04)

[ATTACH=CONFIG]291420[/ATTACH]

---

### Post by #&amp;thj^% on 2022-12-17
this may help, if you show what firefox is used
```
apt policy firefox
```
If it's a snap I'm clueless

---

### Post by peyre on 2022-12-17
It is a snap app, but ironically, you've fixed my problem regardless!  You mentioning it led me to look into fixing snap applications, and I fixed it with 

sudo snap remove firefox
sudo snap install firefox

I've lost my settings, bookmarks, etc., but I can replace all that.

---

### Post by #&amp;thj^% on 2022-12-17
Well we both learned something then. ;)
Good Work peyre.

---

### Post by TenPlus1 on 2022-12-18
Seems that Firefox being a snap is causing more harm than good.

---

