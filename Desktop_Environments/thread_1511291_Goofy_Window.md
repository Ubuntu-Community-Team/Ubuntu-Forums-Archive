---
title: "Goofy Window"
date: 2010-06-16
forum: Desktop Environments
---

### Post by Geek9 on 2010-06-16
how do I get my minimize, maximize and exit buttons on the right of the window instead of the left? 10.04 LTS (latest and greatest)

---

### Post by gchand7 on 2010-06-16
First, you run the gconf-editor and go to apps--metacity--general. There you have "button_layout" option you can modify.

The colon separates what goes to the left and what goes to the right, so the default is "close,minimize,maximize:" you are probably used to "menu:minimize,maximize,close"

---

### Post by howefield on 2010-06-16
Follow the sticky here for the best way...

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by Geek9 on 2010-06-17
thanks man just what I needed, and gc, using gconf is apparently not recommend due to the possibility of messing with future themes.

---

