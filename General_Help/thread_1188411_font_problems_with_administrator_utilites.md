---
title: "font problems with administrator utilites"
date: 2009-06-15
forum: General Help
---

### Post by abethebrewer on 2009-06-15
Just recently many of the configuration utilties in System -> Administration started using a different font. It seems to be the ones that require super user priveliges when they start.  I can't find the setting to get the regular "Sans" font back for these utilities.  This also affects the gdm login screen.  Anything that starts as a non-privileged user has the regular "Sans" font.  Is there a configuration file that I need to clean up?  I have tried deleting all the configuration files in the /root directory, hoping one of them was the culprit.

I have attached a screenshot of a window using the "wrong" font.

---

### Post by thfz on 2009-06-15
Perhaps running gnome-control-center using sudo or su from the terminal and changing the font will help?

---

