---
title: "XScreen Save problems"
date: 2009-02-22
forum: General Help
---

### Post by fearful on 2009-02-22
I just moved from using gnome-screensaver to using the xscreensaver.

Now every time I suspend my computer, when it awakes there is no prompt for password like before, when using gnome-screensaver.

I checked the gconf preferences and they seemed all ok. Any suggestions?

Thanks.

---

### Post by ajmorris on 2009-02-24
> **fearful said:**
> I just moved from using gnome-screensaver to using the xscreensaver.

Now every time I suspend my computer, when it awakes there is no prompt for password like before, when using gnome-screensaver.

I checked the gconf preferences and they seemed all ok. Any suggestions?

Thanks.

Hi there,
to make xscreensaver to prompt for a password, you have to turn on the 'locking' function in the xscreensaver options itself. Now forgive me, it has been quite a while since i ran a screensaver... but iirc, the xscreensaver settings can be accessed by running 'xscreensaver-demo' from either a command line, or the alt-f2 dialog box. If this does not pop-up the settings box, then open up a terminal, and type in: xscreensaver   and press the 'tab' key twice, to show a list of all executable files in your PATH beginning with xscreensaver. One of them will be where you can setup locking. :)

AJ

---

