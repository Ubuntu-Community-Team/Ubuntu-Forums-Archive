---
title: "Docky + emerald graphical problem"
date: 2012-11-19
forum: Desktop Environments
---

### Post by Orignal on 2012-11-19
Hello, this is my first post on the forum!

I am using ubuntu 12.10 with xfce as a desktop environment, compiz with emerald and docky.

Problem:  White frames 1px wide appear around the icons in docky. Docky appears inside a white rectangle when "3d background" option is checked, and a big white rectangle hides a part of the top window when docky hides (this last issue dissapears when hiding is disabled). I have included a screenshot of what it looks like.

What I have tried: 
Changing the icon set, but it doesn't change anything.
I have also tried the different default themes for docky, they all have the same problem.
When switching back to xfwm4, the problem remains.

If I remember correctly, the problem appeared precisely during the installation of the following packages, just before installing emerald:
git autoconf libtool libwnck1.0-cil-dev libwnck-dev intltool libdecoration0-dev gawk compizconfig-settings-manager


Any ideas on what is causing this and how to fix it are welcome! Thanks in advance!

ps: I hope this is the right place to post this question

---

### Post by zombifier25 on 2012-11-20
I think the problem was caused by disabling compositing in Xfwm, Xfce's window manager. Try re-enabling it.

---

### Post by Orignal on 2012-11-20
Thanks for the reply, the problem seems to have disappeared after a couple of reboots (loging out and back in was not sufficient).

I'm going to mark this thread as solved.

---

