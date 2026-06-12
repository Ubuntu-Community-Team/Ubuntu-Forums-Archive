---
title: "Login delay and compiz will not start"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by bucketoftruth on 2007-08-06
This is the second time this happened after I ctrl-backspace'd to kill my windows session.  When I login I see the Ubuntu loading screen with the Gnome Panel and Nautilus icons for about 2 minutes then it pops up some combination of a terminal screen, pidgin, and sometimes another terminal  screen... sometimes nothing... with no window dressings or min/max buttons.  In any case, Compiz doesn't load.  It's in my session items with the command 
```
/usr/bin/compiz.real --ignore-desktop-hints --sm-client-id default0 glib gconf
```
I tried running that from one of the terminal screens and this was the output:
```
gotcha@slim:~$ /usr/bin/compiz.real --ignore-desktop-hints --sm-client-id default0 glib gconf
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```
I also tried starting it with
```
compiz --replace &
```
and got it to start.  However, all my compiz settings have been lost and it defaulted to some other compiz plugins that I never used before.  I tried to change it with the compiz settings manager but nothing sticks.  Help!

---

### Post by bucketoftruth on 2007-08-06
The other thing I've noticed since this started is that I can't change the window setting for mouse-overs.  It's automatically set to raise after 1 second which I do not want.  No matter what I set in System/Preferences/Windows it will not stick.  This leads me to believe that there's some kind of disconnect between what I set and what is written (or read) from the gconf settings.

Anyone have a clue?

---

