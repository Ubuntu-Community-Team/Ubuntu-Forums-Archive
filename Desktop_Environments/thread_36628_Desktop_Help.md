---
title: "Desktop Help"
date: 2005-05-24
forum: Desktop Environments
---

### Post by anp on 2005-05-24
For some reason my ubuntu has been giving me major problems while logging in lately. When I type in the admin used name and password, it starts to load then all of a sudden it comes back to the login screen. I created a test account which seems to load properly. And also when i enter the command prompt from the login screen, the command prompt shows up for a sencond and then it comes back to the login screen. Could someone else help me out with this
thanks

---

### Post by tread on 2005-05-24
Looks like some settings got messed up? If you use gnome, move the .gnome and similar folders somewhere, so when you start it again gnome loads up with default settings.

If you are wondering how to do that when you cannot even login, drop to the console with ctrl-alt-f1 at the gdm login screen.

---

### Post by anp on 2005-05-24
I am a new ubuntu user...
can someone tell me where can i find these .gnome files?

---

### Post by logan2004 on 2005-05-24
in your home folder

does your test account have root access?

if so:
x = your username
y = folders to rename

ls -a /home/x

sudo mv /home/x/y /home/x/y.old

this method will rename the folders so gnome cant find them and creates new ones.

---

