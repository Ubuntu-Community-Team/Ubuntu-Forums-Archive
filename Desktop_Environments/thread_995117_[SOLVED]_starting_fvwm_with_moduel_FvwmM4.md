---
title: "[SOLVED] starting fvwm with moduel FvwmM4"
date: 2008-11-27
forum: Desktop Environments
---

### Post by phorminx on 2008-11-27
I like to have fvwm as an alternative window manager, starting it with the module FvwmM4, i.e., I need to start fvwm with the command

fvwm -cmd "Module FvwmM4 $HOME/.fvwmrc"

What is the cleanest way to achieve this? Should I add a script to
/etc/X11/Xsession.d/
that replaces a call of fvwm by the above line?

---

### Post by jpkotta on 2008-11-27
Put it in ~/.xinitrc.  This will get run if you run startx from the Linux console.  If you symlink this to ~/.xsession```
ln -s ~/.xinitrc ~/.xsession
``` then it will get run if you choose "default session" from GDM/KDM.  ~/.xinitrc is just a shell script.  Your X session ends when ~/.xinitrc ends, so make sure that the window manager is at the end of the script, and that it doesn't fork (don't add an '&').

---

### Post by phorminx on 2008-11-28
Thanks, that's working fine, too!

---

