---
title: "Owner?"
date: 2005-12-08
forum: Desktop Environments
---

### Post by ncab23 on 2005-12-08
I am trying to put an amsnplus folder into my amsn plugin folder, but it says I am not the owner and do not have the privelages to do that. I'm new to ubuntu and linux. What do I do?

---

### Post by taurus on 2005-12-08
Where do you try to put it exactly anyway?  You must put in in ~/ since ~/ means it's your home directory...  In other words, if your login name is jack, then your home directory is /home/jack or is also known as ~.

---

### Post by migueljacq on 2005-12-08
go to your terminal, and type

sudo chown (your user name) (the path of the plugins folder)

i.e sudo chown migueljacq /somefolder/plugins

---

### Post by ncab23 on 2005-12-08
ok great thanks. that worked

---

