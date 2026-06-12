---
title: "urgent! can not open Desktop manager"
date: 2007-01-09
forum: Desktop Environments
---

### Post by dming on 2007-01-09
Hi All,

Due to some incident, I delete the desktop manager from the "Add and Remove" by accident ( I am not aware it is important), So each time I open ubuntu again, I can input username and password, but it will not return me the Desktop but a totally blank screen, I can not do anything with it, even don't know how to recove the system:-# 


Could anyone give some idea how to handle this problem?

Thank you very much at advanced.

Ming

---

### Post by Sqwishy on 2007-01-09
oh i can help you!
next time before you log in, on your keyboard press ctrl + alt + f6 all at the same time, it should take you to a terminal, if it doesn't try ctrl + alt + f5 or f4 etc.
At the terminal type your username and password to log in, then type the following
```
sudo apt-get install gnome
```
that's a assuming you were using gnome, replace it with kde if you use kde, or try gnome and if it doesn't work you can type ' sudo get-apt remove gnome ' to get rid of it and then try kde.

---

### Post by dming on 2007-01-09
Yes, It works.

Thank you very much,
Ming

---

