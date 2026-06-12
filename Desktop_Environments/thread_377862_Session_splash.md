---
title: "Session splash"
date: 2007-03-06
forum: Desktop Environments
---

### Post by Yokaze on 2007-03-06
Alright, I'm new to this whole posting on a forum thing (I generally just read them) so tell me if I'm doing something wrong. I've been trying to change the session splash screen in Edgy and I can't seem to get it to work. I tried using the gconf-editor thing and told it to use the picture I want (A picture of Bayushi Kachiko for those of you who are as nerdy as I) but for some reason it then just displays some sort of Gnome picture that is different from the oringinal Ubuntu splash that I was trying to replace. Any suggestions? Thanks

---

### Post by aysiu on 2007-03-06
Alt-F2 ```
gksudo nautilus
``` Go to /usr/share/pixmaps/splash and replace whatever image is there with your own image.

---

### Post by ardchoille42 on 2007-03-06
> **Yokaze said:**
> Alright, I'm new to this whole posting on a forum thing (I generally just read them) so tell me if I'm doing something wrong. I've been trying to change the session splash screen in Edgy and I can't seem to get it to work. I tried using the gconf-editor thing and told it to use the picture I want (A picture of Bayushi Kachiko for those of you who are as nerdy as I) but for some reason it then just displays some sort of Gnome picture that is different from the oringinal Ubuntu splash that I was trying to replace. Any suggestions? Thanks

From what I understand, you have to put the splash screens in /usr/share/pixmaps/splash. Then you can just go into the gconf-editor apps/gnome-session/options and change the splash_image key to the image you want to use. But, you have to use the proper syntax there:

splash/desired-image-name.png

This works great on Dapper.

---

