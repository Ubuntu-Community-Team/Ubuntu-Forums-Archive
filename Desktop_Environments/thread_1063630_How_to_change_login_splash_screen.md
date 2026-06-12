---
title: "How to change login splash screen?"
date: 2009-02-08
forum: Desktop Environments
---

### Post by gobble on 2009-02-08
Dear all

I use Xubuntu 8.0.4.2 LTS. I do not like the default gdm splash screen and I dunno how to change it. I tried changing the gdm.conf file param "GraphicalTheme=xubuntu-simple" where xubuntu-simple is a folder under /usr/share/gdm/themes, but no luck.

I also tried changing the login sound file played with "SoundOnLoginFile=/usr/share/sounds/purple/00051.mp3" but the changes do not seem to take effect after logout or reboot. 

Thanks very much in advance. 

Regards

---

### Post by Vadi on 2009-02-08
In Gnome, it's System&#8594;Administration&#8594;Login Window&#8594;Local. Maybe it's something similar in xcfe?

---

### Post by x1a4 on 2009-02-08
To change GDM settings (including theme): 

Settings > Login Window

or edit /etc/gdm/gdm.conf-custom

GDM doesn't support MP3s.  Use wav files instead.

To change the Xfce splash screen: 

Settings > Settings Manager > Splash Screen

---

