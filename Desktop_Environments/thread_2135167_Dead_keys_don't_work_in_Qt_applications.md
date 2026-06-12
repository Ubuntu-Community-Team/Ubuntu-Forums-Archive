---
title: "Dead keys don't work in Qt applications"
date: 2013-04-13
forum: Desktop Environments
---

### Post by Steve88 on 2013-04-13
I am not able to use deadkeys in Ubuntu 12.10 when using Qt applications (like Skype). I don't know how to fix this. I am using anthy for japanese and ibus and I installed the ibus-qt package, but that didn't change anything.
I tried googling a solution, but I didn't find any... Can anyone help me?


Best regards,

Stéphane Thibaud

---

### Post by Tk007LwZFJW5ej on 2013-04-27
I'm having the same problem. Did you try:

1. type "qtconfig-qt4" from the command line
2. Qt Configuration should pop up. Go to the Interface tab.
3. At the bottom of the window, under Default Input Method, select ibus.

---

