---
title: "unable to change fonts settings for qt4/kde4 applications"
date: 2009-05-19
forum: Desktop Environments
---

### Post by ra100 on 2009-05-19
Hi all.
I want to change fonts and mainly to disable antialising for qt4/kde4 applications in 9.04. I have installed systemsettings and when i launch it by command "systemsettings", i can see only icons and emoticons in Appearance. Settings for fonts aren´t available. So i'm not able to change it.
Also command "qtconfig" works, but via qtconfig it´s impossible to disable antialising.
Attached snapshot.
I filed a [bug]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/372378"), but no response still.
Anybody help please.
Thanks

---

### Post by ra100 on 2009-05-21
Nobodody knows? :-(

---

### Post by benerivo on 2009-05-21
I'm not sure changing the options in systemsettings will control the font antialiasing of kde4 applications in gnome. To get the extra options in systemsettings, you'll need to install kdebase, which will bring in the basic kde4 desktop parts, such as font control, colour schemes, styles, etc.

---

### Post by ra100 on 2009-05-21
> **benerivo said:**
> I'm not sure changing the options in systemsettings will control the font antialiasing of kde4 applications in gnome.

Yes, it will. It works for me in openSUSE.

> **benerivo said:**
> 
To get the extra options in systemsettings, you'll need to install kdebase, which will bring in the basic kde4 desktop parts, such as font control, colour schemes, styles, etc.

It doesn't help.I have installed also kdebase, but no affect :-(
Font control, colour schemes, styles, etc. aren't available. Still the same.

---

### Post by benerivo on 2009-05-21
Try logging in to a kde session (i think kdebase will be enough to get in to a kde session), then log out and go back in to gnome. I think systemsettings might then be okay.

---

