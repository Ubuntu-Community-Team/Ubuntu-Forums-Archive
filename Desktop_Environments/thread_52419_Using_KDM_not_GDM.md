---
title: "Using KDM not GDM"
date: 2005-07-27
forum: Desktop Environments
---

### Post by redlabour on 2005-07-27
I tried to 

$ sudo dpkg-reconfigure kdm

but it still looks like GDM before. 

How can i change this ?

---

### Post by dave9191 on 2005-07-27
Change your default login manager in the config file. I'm not on my linux laptop atm so i can't give you the full path. Something like /etc/X11/default-login-manager. Just see whats in /etc/X11 and edit the file that sounds right. Just change the gdm to kdm :)

Dave

---

