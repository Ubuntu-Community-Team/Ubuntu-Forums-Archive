---
title: "[SOLVED] Fluxbox font and menu size quetion."
date: 2007-10-24
forum: Desktop Environments
---

### Post by penman242 on 2007-10-24
I'm no expert (which will probably be obvious) but I know I like fluxbox.

I have installed fluxbox on top of a standard gutsy x86 installation.

If I leave gdm enabled, and start fluxbox from gdm screen, fluxbox starts fine but the screen resolution is 1024x768.  Adding "xrandr -s 1280x1024 &" above "exec /usr/bin/fluxbox" in ~/.fluxbox/startup fixed that problem, according to xrandr -q.  The menu, toolbar and all fonts look fine.

If I disable gdm with:

sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K30gdm

reboot and use a ~/.xsession containing "exec /usr/bin/fluxbox" the screen resolution is back to 1024x768.  Adding "xrandr -s 1280x1024 &" above "exec /usr/bin/fluxbox" in ~/.xsession fixed that problem.

But, the menu, the toolbar, and all the fonts anywhere, like in terminal and including what I'm typing right now in geany, look huge, like as though the screen res is 1024x768 perhaps.  Yet xrandr -q says my resolution is 1280x1024.

Possible clue: adding xrandr -s 1280x1024 to ~/.fluxbox/startup only works when gdm is allowed to start.  If gdm is off, xrandr -s 1280x1024 must be in ~/.xsession to work.

A forum search revealed that I can type "startx -- -dpi 70", which works, but isn't there a better way?  Thanks!

---

### Post by RedSquirrel on 2007-10-24
I recommend using **/usr/bin/startfluxbox** in your ~/.xsession (not /usr/bin/fluxbox). startfluxbox is a script that will run ~/.fluxbox/startup (or create the whole ~/.fluxbox directory and contents if they don't exist). GDM is setup to use startfluxbox. That is the reason your startup script is run when you use GDM (see /usr/share/xsessions/fluxbox.desktop).

As for the resolution, I just put my preferred resolution in /etc/X11/xorg.conf and Fluxbox will use it.

I tend to set DPI in ~/.Xresources:

```
Xft.dpi      96
```and load ~/.Xresources in my ~/.xinitrc:

```
xrdb -merge ~/.Xresources
```

---

### Post by penman242 on 2007-10-24
Thanks a bunch RedSquirrel.  Great information!  Can't wait to try it tonight.  I'll post back if I have any issues.

---

### Post by penman242 on 2007-10-24
Everything is working great now.  However I did have to add a colon after Xft.dpi when modifying ~/.Xresources:

```
Xft.dpi:      96
```

to get it to work.  Thanks again!:)

---

### Post by RedSquirrel on 2007-10-25
> **penman242 said:**
> Everything is working great now. However I did have to add a colon after Xft.dpi when modifying ~/.Xresources:

```
Xft.dpi:      96
```to get it to work. Thanks again!

Ah, good catch. It definitely needs a colon. :oops: :grin:

---

