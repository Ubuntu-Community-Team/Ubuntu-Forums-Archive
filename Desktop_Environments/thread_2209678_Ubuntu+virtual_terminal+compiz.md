---
title: "Ubuntu+virtual terminal+compiz"
date: 2014-03-06
forum: Desktop Environments
---

### Post by bobbyallen9292 on 2014-03-06
I'm wondering the command line to start ubuntu in a virtual terminal to use only the unity profile in CCSM and not my custom compiz profile.

currently i can access it through startx gnome-session -- :1 vt8 by changing the desktop environment by using 
gsettings set org.gnome.desktop.session session-name ubuntu
that uses my custome compiz profile and not the unity profile.


Thanks in advance.

---

### Post by bobbyallen9292 on 2014-03-07
I'm sure this was answered before. I was able to put exec unity in my xinitrc file thanks.

---

