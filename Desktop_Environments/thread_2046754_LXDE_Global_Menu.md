---
title: "LXDE Global Menu"
date: 2012-08-23
forum: Desktop Environments
---

### Post by viperdvman on 2012-08-23
Does anyone have or know where to get the [COLOR="Red"]lxglobalmenu.tar.gz[/COLOR] file? The main source of it ([COLOR="Blue"]http://home.student.utwente.nl/j.vanderhoff/downloads/lxglobalmenu.tar.gz[/COLOR]) is down, and every Google for LXDE Global Menu or something to that effect points to this broken link.

It does suck, that site seems to be the only source of getting a global menu in LXDE without having to install the unity-2d-panel.

---

### Post by nyamina on 2012-08-23
> **viperdvman said:**
> Does anyone have or know where to get the [COLOR=Red]lxglobalmenu.tar.gz[/COLOR] file? The main source of it ([COLOR=Blue]http://home.student.utwente.nl/j.vanderhoff/downloads/lxglobalmenu.tar.gz[/COLOR]) is down, and every Google for LXDE Global Menu or something to that effect points to this broken link.

It does suck, that site seems to be the only source of getting a global menu in LXDE without having to install the unity-2d-panel.
I second this massively. Apparently it's totally easy to make applets too. If only I was a programmer, I'd have done it myself.

It's not much of a solution, but if you already have Gnome-Classic, or Gnome, or Unity with gnome-panel installed, there is a ppa you could use that adds a straight-ahead global menu applet, since gnome-panel works pretty well in LXDE: 
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install indicator-applet-appmenu
```Or, an easier solution, you could actually install the XFCE panel, and install the global menu for that: I know it's also not LXDE, but then again Lubuntu apparently uses a few bits and bats from XFCE all over the place. I think eve[SIZE=2]n Lubuntu's power management and mixer apps are actually XFCE's. So, it's not too far off =) it shouldn't bring in the rest of XFCE.
[/SIZE]                                   ```
sudo apt-get install xfce4-panel
sudo apt-add-repository ppa:the-warl0ck-1989/xfce-appmenu-plugin
sudo apt-get update && sudo apt-get install xfce4-appmenu-plugin indicator-appmenu appmenu-gtk appmenu-qt

```
(edit: I don't know why the formatting on this post kept messing up...)

---

### Post by ankspo71 on 2012-09-01
Try this link: (Hopefully it is the same package you are looking for)
[http://aduteca.adunanza.net/User:bruce_wayne](http://aduteca.adunanza.net/User:bruce_wayne)

According to the link below, it will require "globalmenu-server" to work, which is part of gnome-globalmenu.

[http://sourceforge.net/mailarchive/forum.php?thread_name=4D70FA8D.3010400%40gmail.com&forum_name=lxde-list](http://sourceforge.net/mailarchive/forum.php?thread_name=4D70FA8D.3010400%40gmail.com&forum_name=lxde-list)

---

### Post by Tekmoor on 2012-10-24
I wonder if anyone's got this working?  If not, I wonder what the next best light-weight solution would be, xfce panel in lxde?

Edit: it appears the app menu isn't working in xfce anymore: [https://bugs.launchpad.net/xfce4-appmenu-plugin/+bug/922615](https://bugs.launchpad.net/xfce4-appmenu-plugin/+bug/922615)

---

