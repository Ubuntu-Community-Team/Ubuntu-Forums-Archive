---
title: "default user settings skeleton or profile"
date: 2008-05-23
forum: Desktop Environments
---

### Post by gkffjcs on 2008-05-23
I use my computers in a way that causes me to frequently have to deal with working in a new default user. This is annoying. I would like to change the default user profile/skeleton or what ever it happens to be called, so that when I create a new user and log in the first time the configuration I have specified will be copied to the new user's home and I well not have to recreate all of my settings and tweaks. More importantly I would like to prevent the system from creating a ~/Music ~/Pictures ~/Templates ~/Public and instead cause the system to create a ~/Documents/Pictures and so forth, with all the default folders.

---

### Post by jpkotta on 2008-05-24
Look at /etc/skel.  New users' $HOMEs are copied from there (at least when you use adduser).

---

### Post by airmorris on 2009-12-10
Did this work for you? I am trying to do the same thing using Ubuntu Remix for netbooks.

---

### Post by Zorael on 2009-12-11
In the case of default folders, they're specified in **/etc/xdg/user-dirs.defaults**.

---

