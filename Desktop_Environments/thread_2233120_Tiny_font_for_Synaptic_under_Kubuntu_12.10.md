---
title: "Tiny font for Synaptic under Kubuntu 12.10"
date: 2014-07-06
forum: Desktop Environments
---

### Post by pwabrahams on 2014-07-06
I'm running Kubuntu 12.10, and Synaptic (among other programs) comes up with a tiny 9-point font.  I've gone into System Settings (many times) and under "Application Appearance" I've specified:
 (a) System font is Ubuntu 11
 (b) Widget style is Oxygen-gtk (the default)
 (c) Use my KDE fonts in GTK+ applications. 
In most contexts I do get the Ubuntu-11 font, but not all.  The font setting within Synaptic doesn't help.

How can I get Ubuntu 11 to be used everywhere?

---

### Post by Erik1984 on 2014-07-06
I have the same problem (I don't use Synaptic on Kubuntu but have seen this with other GTK apps)
[http://ubuntuforums.org/showthread.php?t=2228079](http://ubuntuforums.org/showthread.php?t=2228079)

---

### Post by speartip on 2014-07-07
2 things to try.
1st change the application font in synaptics preferences.
2nd Because synaptic is a root application, try changing roots fonts. In a terminal:
```
kdesudo systemsettings
```
then change the fonts in application appearance.

---

