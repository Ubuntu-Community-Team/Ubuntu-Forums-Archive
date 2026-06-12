---
title: "Window Title Bar"
date: 2009-08-30
forum: Desktop Environments
---

### Post by jazzman67 on 2009-08-30
I'm running Xubuntu 9.04 with compiz-fusion. The window title bars show fine when opening and closing applications normally. However, when i run an opengl project within the Eclipse IDE, my project have no window title bar and cannot be moved. I'm 100% positive it is not the code or eclipse setup. I have ran the same code on other Xubuntu/Eclipse systems. but never with one with compiz fusion. Any ideas of a fix? Also Emerald is my decorator.

---

### Post by earthpigg on 2009-08-30
compiz is somewhat buggy, and emerald even moreso.

when you are running the software that doesn't play well with it, put xfce back in charge of being your WM instead of compiz/emerald.

in ubuntu with metacity as the window manager (wm), the command is 'metacity --replace' to put gnome's metacity wm in charge, and then 'compiz --replace' to put compiz back in charge.

'xfwm4' is the xubuntu window manager.

try this:

alt+f2

> xfwm4 --replace
or
> xfwm4

then, to put compiz back in charge:

alt+f2
> compiz --replace

if neither 'xfwm4 --replace' nor 'xfwm4' work, then try reading 'man xfwm4' to see what the correct argument is. you will know it works because your screen will flicker, and then all the fancy compiz effects will vanish until you type 'compiz --replace' to bring them back. 

alternatively, any other xubuntu users want to let the OP know exactly what the command is?


this procedure is what many gamers do. disable compiz, play game. finish playing, turn compiz back on.

---

### Post by jazzman67 on 2009-08-30
This will work for me!! Thanks alot earthpigg!

---

