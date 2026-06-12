---
title: "1680x1050 resolution? I missed where it asks, should I just reinstall?"
date: 2006-01-15
forum: General Help
---

### Post by sitheris on 2006-01-15
I just installed Ubuntu on a spare machine today.  Normally it asks you what resolutions you'd like to use, where I normally pick 1680x1050 since I have a Dell 2005fpw.  

However, I was afk during the install and came back to my computer to a login screen.  Apparently it went ahead and accepted the defaults since I wasn't there.  

Is there a way I can get the option of 1680x1050 without reformatting?

Thanks.

---

### Post by aysiu on 2006-01-15
Yes.
Control-Alt-F1
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sitheris on 2006-01-15
nvm I just fixed it by editing xorg.conf

---

### Post by mofomikeman on 2006-01-15
[QUOTE=sitheris]nvm I just fixed it by editing xorg.conf[/QUOTE]
Thats what the above post said to do...

---

### Post by sitheris on 2006-01-15
[QUOTE=mofomikeman]Thats what the above post said to do...[/QUOTE]

I didn't have the thread refreshed before I posted.

---

### Post by learning curve on 2006-01-15
Just go to system/Preferences/Screen resolution and change it.  The only screen that will be at the highest resolution will be the login screen.
Learning Curve:cool:

---

