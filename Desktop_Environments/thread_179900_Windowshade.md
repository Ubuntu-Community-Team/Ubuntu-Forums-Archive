---
title: "Windowshade?"
date: 2006-05-21
forum: Desktop Environments
---

### Post by flip314 on 2006-05-21
On Ubuntu the default behavior for double-clicking on a window title bar is to maximize/unmaximize it.  How do I change that so that it rolls up the window into the titlebar instead?

edit:  sorry.  I should have looked harder. System>Prefs>windows had what I needed *sheepish*

---

### Post by aysiu on 2006-05-21
System > Preferences > Windows > Titlebar Action

---

### Post by bluevoodoo1 on 2006-05-21
system tools > configuration editor

apps > metacity > general

change the first entry of action_double_click_titlebar to "toggle_shade"


EDIT: Thanks aysiu I didn't know you could do it there!

---

### Post by Nano Geek on 2006-05-21
Go: **System**>**Preferences**>**Windows**>and find where it says **Double-click on titlebar to perform this action** and change it to **Roll up**. That should do it. :)
[Edit] Sorry guys, can't seem to write it fast enough.

---

### Post by RJNFC on 2006-06-02
Using a fresh Dapper install (not an upgrade).  My option for this is greyed out in System>Preferences>Windows> and changng it in gconf has no effect.  Anyone else have this problem and/or a solution?  I love shading windows :(

---

