---
title: "error in gdm.conf-custom file"
date: 2007-03-19
forum: Desktop Environments
---

### Post by rx29g on 2007-03-19
I'v  edited the file /etc/gdm/gdm.conf-custom and made an error in on of the [Server-Xgl] lines.
system will not load in X mode now.
What command do I use to edit the file and correct the error?

thks.

---

### Post by twikletoes on 2007-03-21
I suggest that you undo your file and try again.
This can be achieved by hitting Ctrl + alt + F-1-6 and editing you gdm file thing.
you won't be able use gedit but you can use nano
you would type sudo nano -w (the w is so you don't just type off the screen to the end of the world.) /etc/gdm/gdm.conf-custom
then undo what you did and try another way at doing it.

---

