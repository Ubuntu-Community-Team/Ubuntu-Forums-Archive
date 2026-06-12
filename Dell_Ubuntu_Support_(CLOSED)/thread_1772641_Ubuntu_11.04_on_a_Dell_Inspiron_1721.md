---
title: "Ubuntu 11.04 on a Dell Inspiron 1721"
date: 2011-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TigrisAltaica on 2011-05-31
Hi! I've succesfully installed 11.04 on my Inspiron 1721, but if I try to load the system with anything more than classic ubuntu with no effects, I just get the wallpaper and the mouse pointer and can do anything from there. Is there anything I can do to fix this? Many thanks.

---

### Post by garvinrick4 on 2011-05-31
```
/usr/lib/nux/unity_support_test -p 
```
Run this above in a Terminal first and see if you are 3D capable if all says yes then post back:

---

### Post by TigrisAltaica on 2011-05-31
I ran the command, everything came back as yes.

---

### Post by garvinrick4 on 2011-05-31
When you log into Unity interface:

ctrl/alt/F1  and log in and password:
```
sudo apt-get install compizconfig-settings-manager
```
```
unity -reset
```
ctrl/alt/F7
```
ccsm
```
Make sure Ubuntu unity plugin is checked.
That should set things straight:

---

### Post by TigrisAltaica on 2011-05-31
Working now. Thanks!

---

### Post by garvinrick4 on 2011-05-31
>  			 		   		 		 		Working now. Thanks!

You got it, enjoy your Ubuntu.

---

