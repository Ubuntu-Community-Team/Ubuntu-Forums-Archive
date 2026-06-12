---
title: "Xfce looks ugly after manual upgrade"
date: 2013-01-29
forum: Desktop Environments
---

### Post by TheHimself on 2013-01-29
I just manually upgraded Xubuntu from maverick to precise and it is working fine. Just the Gnome applications look ugly and I can't change their appearance from XFCE settings. I've attached a screenshot. Also where is the panel which was used in the xubuntu live disk? My panel is the old one.

Somewhat unrelated but I have both emacs23 and 24 installed but only 23 can be run! :confused:

---

### Post by adam.stokes on 2013-01-29
Maybe install **gtk-theme-switch** and selecting a gtk theme from the gui will make the gnome applications look a bit nicer.

---

### Post by Frogs Hair on 2013-01-29
The old themes might not be compatible so you are seeing the default root theme. 10.10 I think came with XFCE 4.6 and 4.8 or 4.10 is in use on 12.04.

---

### Post by TheHimself on 2013-01-30
gtk-theme-switch didn't help. 
How can I install the new themes? I can't find xfce themes in synaptic.

---

### Post by LewisTM on 2013-01-30
Between 10.10 and 12.04, most GNOME programs have transitioned from GTK2 to GTK3. So if you have an old GTK2 theme selected, the GNOME apps will not be themed and will look ugly. 

The solution is to pick a GTK theme that provides both version 2 and 3. Greybird is one which you will find in Settings->Appearance. You can get more from xfce-look.org or gnome-look.org, just make sure you download GTK2/3 flavors. You can also try these [5 GTK2/3 themes]("http://www.webupd8.org/2012/01/spice-up-your-desktop-with-these-5-cool.html").

Cheers!

---

### Post by TheHimself on 2013-01-30
Thanks a lot. I installed clearlooks-phoenix and it now looks good.

---

