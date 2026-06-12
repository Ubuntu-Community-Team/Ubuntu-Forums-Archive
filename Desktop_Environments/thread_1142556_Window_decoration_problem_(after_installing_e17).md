---
title: "Window decoration problem (after installing e17?)"
date: 2009-04-29
forum: Desktop Environments
---

### Post by VCoolio on 2009-04-29
Hi, I've (successfully) installed e17 / Enlightenment on Jaunty. Logged into it, messed around etc. Point is, it uses gtk for drawing windows, except the window borders. The window borders are drawn by e17 itself.

Now, when I login into Gnome again, my window decoration is gone. Trying metacity / compiz --replace and all gives me this error:

gtk-window-decorator: symbol lookup error: /usr/bin/gtk-window-decorator: undefined symbol: decor_blend_border_picture

I'm using emerald now. But how can I solve the real problem? Btw I'm just assuming installing e17 is the problem (or maybe just ecomorph / ecomp), since that is what has changed.

---

### Post by Deafboy on 2009-08-16
I have also noticed problems with gtk-window-decorator in gnome after installing emorph to e17.
But i get different error message:

```
deafboy@deafboy-notas:~$ gtk-window-decorator 
gtk-window-decorator: error while loading shared libraries: libdecoration.so.0: cannot open shared object file: No such file or directory
```
libdecoration0 is installed

Also when trying to turn on decoration in CCSM it writes:
```

compiz.real (core) - Error: Couldn't load plugin 'decoration'
```

___________________________________________________________________
Ubuntu 9.04

---

### Post by Deafboy on 2009-08-16
Solved by removing every part of compiz manualy and installing it back. After that i had to turn on compiz plugins (all has been disabled, but configuration of each was like before, so don't need to reconfigure)

---

### Post by silverglade00 on 2010-01-26
> **Deafboy said:**
> Solved by removing every part of compiz manualy and installing it back. After that i had to turn on compiz plugins (all has been disabled, but configuration of each was like before, so don't need to reconfigure)

THANK YOU!!! That has been bugging me for a week. FWIW, I only had to reinstall everything compiz related through Synaptic and then turn on window decorations in CCSM. Everything else was still enabled for me.

---

