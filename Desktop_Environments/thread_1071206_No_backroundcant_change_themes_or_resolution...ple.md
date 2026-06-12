---
title: "No backround/cant change themes or resolution...please help!"
date: 2009-02-15
forum: Desktop Environments
---

### Post by edubs428 on 2009-02-15
So i've been having this problem for a while and cant find anything in the forums... I know at one point I had the ability to change my backround image and themes and screen resolution, but not anymore. I have tried reinstalling compiz and all things related, i reinstalled the desktop env. and everything. This machine was built for me and I'm not even sure what version of ubuntu i'm running or anything. can someone help?

Thanks!
Erik

---

### Post by itang sanjana on 2009-02-16
For your Ubuntu release just type in terminal
```
lsb_release -a
```

So, what happen when you try to change the background recently?

---

### Post by edubs428 on 2009-02-16
nothing... the color changes, but no picture. also i cannot change themes... my gf said something about how she "might" have installed some kde stuff while poking around, but shes not sure. I have gnome and ubuntu 8.04  ;) thanks for the tip)  I feel so lost with this now... any thoughts? 

Also, I have run compiz check and all is well...

---

### Post by slashank on 2009-03-13
> **edubs428 said:**
> nothing... the color changes, but no picture. also i cannot change themes... my gf said something about how she "might" have installed some kde stuff while poking around, but shes not sure. I have gnome and ubuntu 8.04  ;) thanks for the tip)  I feel so lost with this now... any thoughts? 

Also, I have run compiz check and all is well...

Was the application gtk-kde4 ([http://www.kde-apps.org/content/show.php/gtk-kde4?content=74689)?](http://www.kde-apps.org/content/show.php/gtk-kde4?content=74689)?)
Removed it and removed /etc/gtk-2.0/gtkrc file which was linked to `kde4-config --localprefix`/share/config/gtkrc

Everything works fine now.

---

