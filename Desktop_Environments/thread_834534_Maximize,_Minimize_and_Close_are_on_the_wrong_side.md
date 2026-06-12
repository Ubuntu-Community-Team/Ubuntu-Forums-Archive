---
title: "Maximize, Minimize and Close are on the wrong side of the window."
date: 2008-06-19
forum: Desktop Environments
---

### Post by aknisely on 2008-06-19
I've been messing around with my themes and some how have managed to change the orientation of my maximize, minimize, and close buttons from the right side to the left side. I cannot figure out how to get them back to the right side. Can someone help me? Thanks!

---

### Post by Spyros_Gre on 2008-07-16
Hello my friend! According to [this]("http://ubuntuforums.org/archive/index.php/t-19413.html") you open a terminal, type in gconf-editor then in the tree on the left you need to go to /apps/metacity/general/
There is then a key in the right pane called "button_layout"
edit this key so that it reads:


close,minimize,maximize:menu   //if you want x-# on your left 
menu:minimize,maximize,close   //if you want -#x on your right

---

