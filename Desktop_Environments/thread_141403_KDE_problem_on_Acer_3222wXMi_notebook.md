---
title: "KDE problem on Acer 3222wXMi notebook"
date: 2006-03-08
forum: Desktop Environments
---

### Post by palo73 on 2006-03-08
Hi, 

I've installed Kubuntu 5.10 on my acer notebook (with some problems but i did), linux work, i can boot, i have text console, but i have problem to start kde. when i start it i'll receive just a black screen. Anyway, with kubuntu i have been more successful during the installation as with other distros (FC4, Debian sarge, mandrake 10) 

palo73

---

### Post by Single on 2006-03-08
I also had blank sceen when i started using Ubuntu.

This is what works for me:

Edit the file xorg.conf with this command in the text console:
```
sudo nano /etc/X11/xorg.conf
```

There should be a "Section Device" which contain a line `Driver      "ati"` .

Add this line in the section:
```
Option	    "MonitorLayout" "LVDS,AUTO"
```

---

