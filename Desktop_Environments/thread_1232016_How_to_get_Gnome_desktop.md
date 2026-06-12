---
title: "How to get Gnome desktop?"
date: 2009-08-05
forum: Desktop Environments
---

### Post by zaurus on 2009-08-05
Hello

I just installed Ubuntu 9.04 from minicd. First boot eas in command line prompt. I installed gnome via apt-get install. I run startx and get a GUI but it is not Gnome. How can get Gnome?

KR

---

### Post by Copernicus1234 on 2009-08-05
Sorry, I dont have any experience with the minicd. Hopefully someone else has.

Good luck!

---

### Post by AndyCee on 2009-08-05
What about

sudo apt-get install gnome-desktop
?

---

### Post by pmla on 2009-08-05
sudo apt-get install ubuntu-desktop
then run startx

---

### Post by braete on 2009-08-05
read [this]("http://ubuntuforums.org/showthread.php?t=1155961").
it should help you

or you can do as pmla suggested. that will give you a "full" ubuntu installation

---

### Post by pmlxuser on 2009-08-05
+1 pmla

you then can do

```

$ sudo dpkg-reconfigure gdm

```
to configure to have the GUI start aoutomatically

---

### Post by zaurus on 2009-08-06
Thanks everybody!
Your advices worked perfectly. Still need to figure out as how to fix the standard ubuntu behavior for users accounts. My standard user cannot performs some sudo tasks. I need to use the root account for that. I created root account during install process and that was my mistake.

---

