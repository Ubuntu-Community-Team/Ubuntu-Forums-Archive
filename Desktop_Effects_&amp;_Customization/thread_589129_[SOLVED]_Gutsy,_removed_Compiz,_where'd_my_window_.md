---
title: "[SOLVED] Gutsy, removed Compiz, where'd my window borders go?"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by Arthur Archnix on 2007-10-23
Hi, fresh gutsy install, and removed Compiz and all that jazz since I just want to run metacity. Unfortunately, after removing it I have to manually run metacity --replace or else add that to my session options to get it to start up. I don't want to add it to my session options, I want the old Feisty behaviour. Is there a config file I have to edit so that metacity is started up with my gnome session?

Update: Actually, I just tried adding metacity --replace to my session startups, just while I'm waiting for the right way to do this, and it doesn't work! What!?

---

### Post by Arthur Archnix on 2007-10-27
bump

---

### Post by Arthur Archnix on 2008-01-16
Just going through all my old threads and trying to clean them up. Then answer for this is to change the default window manager from compiz to metacity via gconf-editor.

In a terminal type:
```
gconf-editor
```
Then hit search, type window and hit enter. Then click on this:
```
/desktop/gnome/applications/window_manager
```
Then click on the "default" and change from:
```
/usr/bin/compiz
```
to
```
/usr/bin/metacity 
```

---

