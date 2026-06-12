---
title: "When I use xrandr to increase the screensize, Openbox's fonts become huge."
date: 2009-06-04
forum: Desktop Environments
---

### Post by learningcurb on 2009-06-04
I'm trying to run a minimal Openbox install of Ubuntu inside of VMWare player.  I can't seem to get the resolution configured properly however.  I can get into X Windows with startx and use Openbox at the default resolution which is pretty small.  So I use xrandr -s 1600x1200 to resize the display to 1600x1200 and everything works fine until I restart openbox or switch to fluxbox.  When do this the window decorations and and screen fonts become huge.  Oddly enough though, the fonts inside of xterm look normal.  I tried xrandr --dpi 96 and other settings but the window managers ignore this setting.  If I reset the resolution with xrandr -s 800x600 and then restart openbox, then the DPI goes back to normal.  But this seems like a really bad workaround.

When I do xrandr -s 1600x1200, xdpyinfo | grep dots reports 192x192 dots per inch.  If I do xrandr 800x600 it goes back down to 96x96.

I've tried searching everywhere and I can't seem to get xorg to cooperate.  I have noticed that this problem went away after I installed gdm and xfce, but I want to keep the system as minimal as possible so I would like to avoid that if possible.

Ideally I would like to set up the resolution and DPI settings manually.  The /etc/X11/xorg.conf is mostly empty, so I am not sure which edits to make.

---

