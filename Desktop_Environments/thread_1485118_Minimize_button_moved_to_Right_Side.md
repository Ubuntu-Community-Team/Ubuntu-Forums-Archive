---
title: "Minimize button moved to Right Side"
date: 2010-05-16
forum: Desktop Environments
---

### Post by BalaViknesh on 2010-05-16
After the latest update in Lucid, the Minimize adn maximize and close button moved to Righ hand side.

can anyone tell me how to change this.

---

### Post by lindsay7 on 2010-05-16
You need to enable the"configuration editor" first.  Right click on the applications menu at the top right of your screen and click on edit menu. Go down to system tools and click on it, check on the configuration editor.  After you do that. Open the config editor and click on apps. Then click on metacity. then click on general. Then click on button_layout.  You can set this to change how  and where the buttons are.

---

### Post by BalaViknesh on 2010-05-16
thanx a ton lindsay

---

### Post by Grumbel on 2010-05-16
The command line way of fixing it:

 gconftool --type string --set /apps/metacity/general/button_layout close,menu:minimize,maximize

---

### Post by drs305 on 2010-05-16
And just to elaborate, if it isn't obvious, with either method:

Items to the left of the colon ( : ) will be on the left side of the window, items to the right of the colon will be to the right side. Items on the same side should be separated by a comma ( , ). You can also add a "spacer" between items, such as " close,spacer,minimize,maximize: "

---

### Post by Clancy_s on 2010-05-17
Upgrading to LL moved *my* buttons from the right to the left :rolleyes:

Fortunately the fix works both ways: thanks to all. :)

---

