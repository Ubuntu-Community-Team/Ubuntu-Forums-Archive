---
title: "Xserver crash, blinking display"
date: 2006-06-12
forum: Desktop Environments
---

### Post by wleljo on 2006-06-12
Good morning:
Please, help me! my files are under threat!

When I boot ubuntu, it starts but at the end of start up the window blinks, and never stops. It can't open login page.

I booted in a recovery mode, but couldn't start xserver.

Yesterday I had installed newer version of glib, freetype font, at /usr. May be it is the cause?

thank you for support in advance!

---

### Post by stilus on 2006-06-12
First of all, don't panic. Your files are not under threat. Linux is not windows, you do not need the GUI for it to work... What you could try to do, just to get some more info, is drop to a console with CTRL+ALT +F1. Log in, and look at /var/log/Xorg.0.log What does it tell you? 
Secondly, did you install a glib version from the repositories, or from some other source? fiddling with glib might not be the best thing to do when you are not completely comfortable with your linux system (yet). 
So, before anyone can help you, you might want to run through the logs (/var/log/messages might be a good place to go look as well) and see if it is reporting some kind off error that could explain your problem. 
good luck!

---

### Post by wleljo on 2006-06-13
thanks for your reply!
does linux has anything like "restore" or "repair" function in windows?

I may re-install ubuntu; if I do it, does it clear and remove all directories (/usr, /home, etc.)?
Can I install linux and keep old files? 

once again I appreciate your help

---

