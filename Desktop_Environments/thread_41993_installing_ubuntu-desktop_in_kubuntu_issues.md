---
title: "installing ubuntu-desktop in kubuntu issues"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Devilotx on 2005-06-15
I wanted to try Gnome, since I've never really been a fan of it, but I do like Kubuntu for the desktop, So I issued the command sudo apt-get install ubuntu-desktop to install it, it shows in my sessions of the KDM, but when I load it I'm missing the gnome panel and most of the desktop icons except for firefox and my documents.

I have to cntrl+backspace back to KDM to get into KDE

I've checked and Gnome-panel has been installed... it just doesn't seem to be working.

---

### Post by codejunkie on 2005-06-15
i've noticed things like this when installing ubuntu first then kubuntu. everything seems to work fine for me if i do a clean install and then install both environments. or by creating a new user account and logging in as that user im thinking it might be permissions issues for first user account being changed or something. so you could try creating a new user account and login to gnome with that user it might fix it.

---

### Post by Klin'Targ on 2005-06-15
Try try removing/moving these directories from your home directory:
.gnome
.gnome2
.gconf
.gconfd

---

### Post by Devilotx on 2005-06-16
Ok, So I booted into Xandros 3 (I dual boot) and removed the 

.gnome
.gnome2
.gconf
.gconfd

Folders and booted, I still had no panels, but  I apt-get install Gnome-panel and this time it works :-D

Good tidings to you all,

And thanks

---

