---
title: "Resolution Troubles :("
date: 2008-02-02
forum: Desktop Environments
---

### Post by androidpatty on 2008-02-02
Hi, let me explain what i have done so far:

* I have installed ubuntu gusty gibbon
* I have installed (successfully) the openchrome drivers to support my VN800 chipset.
* I have changed the xorg.conf file to use the "via" driver (updated by the stage previous) instead of the "vesa" driver (a generic one, i think?)
* Everything worked wonderfully and I could see the screen, but it was in 800x600 (my monitor goes up to 1280x800 in windows xp)
* I tried to change it, but it was using a generic monitor (or something like that).  So i changed to a generic monitor that supported my resolution (LCM Monitor 1280x800).
*I then set the resolution, and chose the only refresh rate available (60Hz) which im pretty sure was right.

Now, the login screen displays perfectly in 1280 x 800, but when i log on it all goes very jumpy. although you can just about make out a mouse moving around the screen.

Does anybody know how to fix this?

---

### Post by taurus on 2008-02-02
Maybe you need to get the horizontal and vertical refreshing rates of your monitor and add them to /etc/X11/xorg.conf.

---

### Post by androidpatty on 2008-02-02
Thanks for the reply.  I have tried to find those details, but I cant find them anywhere - im using an AMILO Pro v2055 laptop.  They dont seem to like to tell you about specific hardware specifications.

Plus, why would the login screen work perfectly if this was the issue?

EDIT:-

On testing, I have found that if i change the session to "FAILSAFE terminal", and then run the commands :

sudo su
gnome-session

everything works perfectly - gnome appears, and is rendered at 1280x800!

Interestingly, it doesnt work without the sudo su command.

---

