---
title: "cannot log into gnome after supposed hard reset"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Dummies102 on 2005-12-18
Hello all. As of right now, I cannot log into the gnome desktop. I can log into KDE, but once there I can't open any gnome programs, such as the gnome-system-monitor and firefox.

Two things happened before this problem arose: I came back to find my computer at the GDM, so I assume there was a power loss, but not certain. Also, that day I had installed KDE and KDE-dev. 

I've searched around but couldn't find any posts on this. If there's any other information anyone needs, please tell me.

Thanks.

---

### Post by Knomefan on 2005-12-18
Hm, did you try to start Gnome in safe-mode?
You could also try to just start an xterm from GDM and start gnome-session from there. This way you should be able to see what is causing the problem.

I'd suspect that it is some of the config files for gnome got somehow corrupted, so moving them out of the way (for example .gconf, .gnome2, etc.) might solve the problem, but you will of course loose your settings.

Did you try to start gnome with a different/new user to see if it works there?

---

### Post by Dummies102 on 2005-12-19
here's where I am. I can log into gnome with a different user just fine. I can log into xterm with my account and start gnome-session from there just fine (although I seem to have lost of window manager). However, futsing with my config files does nothing. I suppose I have to fix GDM now? any place I should start?

---

