---
title: "Desktop-icons missing sometimes"
date: 2011-08-21
forum: Desktop Environments
---

### Post by JohnFante on 2011-08-21
I have a peculiar problem.

Sometime (once every 4-5 time) when I boot my machine the desktop icons are missing and I have to log out and in again to get them back.

Besides that the systems works fine.

I am running Natty 64 bit with a GTX275 graphicscard and the latest drivers from X updates.

You can see the problem illustrated below.

It looks like som kind of compiz related problem.

Any suggestions?

---

### Post by dino99 on 2011-08-21
into a terminal, either:

gnome-panel --replace &
metacity --replace &

---

### Post by JohnFante on 2011-08-21
Thank you. 

But is there not a more permanent fix than restarting metacity every time?

---

### Post by Pirate Zoro on 2011-08-21
Not the most elegant fix, but you could try creating a script with the command to restart metacity and add it to your startup programs.

---

