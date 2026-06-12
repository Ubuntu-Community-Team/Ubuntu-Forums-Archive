---
title: "Changes in dconf-editor don't take effect"
date: 2014-02-11
forum: Desktop Environments
---

### Post by paulhinterberger on 2014-02-11
Hey,
So after a long time resisting the update from 11.04, I now installed ubuntu 13.10, and a mate gnome 2 fork because I don't like the gnome 3 classic version.
So far so good, I installed compiz config manager and have the look and feel back to what I am used to.
Now I have some issues that I tried to solve with the dconf-editor but it doesn't seem to take effect:
1. Whenever I come back from suspend I get asked for the password, even though I unchecked that in the dconf editor
2. When I close the laptop lid, it suspends, even though I changed that to blank screen in both the system preferences and dconf 
I don't know what to do here.
Also when I start dconf I get the following warning twice, don't understand if they are related:
** (dconf-editor: 6902): WARNING **; dconf-schema. val a 330: Unknown property on <schema>, extends

Hope someone knows what's going on,
Thanks already!

---

### Post by buzzingrobot on 2014-02-11
Compiz and MATE 1.6 have issues getting along.  Check the forums at mate-desktop.org

Be sure you are using the MATE section in dconf. And, you do have the "lock screen when screen saver active" option deselected?  It's in the Screensaver preference panel. (I deactivate the screensaver and disable it as a startup program.)

---

### Post by paulhinterberger on 2014-02-11
hey, thanks for the quick answer!
I did all that, didn't help...
Ill try in the mate forum, maybe they know. 
cheers

---

### Post by buzzingrobot on 2014-02-11
Good luck.  If the Gnome power management daemon is running at startup, as well as the comparable MATE daemon, try disabling it.

---

