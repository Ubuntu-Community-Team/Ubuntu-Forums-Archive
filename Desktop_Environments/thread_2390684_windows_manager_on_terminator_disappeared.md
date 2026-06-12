---
title: "windows manager on terminator disappeared"
date: 2018-05-01
forum: Desktop Environments
---

### Post by kaky951357 on 2018-05-01
Hello folks,
i recently installed terminator (the terminal emulator) when trying to personalize it, i clicked on something that made the windows manager barre disappear (no more close minimize maximise buttons on the top right ) i removed, purged , re-installed and nothing.
Thank you for trying to help have a good day.

---

### Post by ank2 on 2018-05-01
Sounds like the window manager crashes. After a while it should reload itself and restore everything.

There should be a ~/.xsession-errors telling you what's wrong.

---

### Post by Habitual on 2018-05-01
Method 1:
close terminator
Ctrl+Al+T should give you Ubuntu's terminal utility.
Now issue 
```
rm -fr ~/.config/terminator/ && exit
```
Start terminator.

Method 2:
Close terminator.
File Manager > Crtl+H to show hidden.
Navigate from "home" into .config/ and remove terminator/
Start terminator.

---

### Post by #&amp;thj^% on 2018-05-01
You may want to try just right clicking in the terminator window.>>>and select preferences>>>look at the global tab>>>and make sure Window Borders is ticked.

---

