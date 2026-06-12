---
title: "Jaunty scrambled keyboard in VNS Session"
date: 2009-04-28
forum: General Help
---

### Post by frostbite4783 on 2009-04-28
Hey I just updated from 8.10 to 9.04 and afterward when I fire up my VNC client on my headless server, the key layout was incorrect.  Instead of qwerty, I was displaying c.gvn.  I looked out the keyboard layout and I am using the 105 keyboard which is correct and I can SSH into my machine without any issues, it's only my VNC that's having issue.  I am using xtightvnc server for my VNC funness.  If anyone is also having problems and found a solution, please help me.

---

### Post by Sephian on 2009-04-30
I edited my .vnc/xstartup.  Specifically remarking out /etc/X11/Xsession and adding the last 3 lines.





#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
#/etc/X11/Xsession

nautilus &
gnome-panel &
xterm &

---

### Post by frostbite4783 on 2009-05-07
yeah I edited my xstartup file to make what you have and I'm still having the same problem.

---

### Post by mgatliff on 2009-05-27
> **Sephian said:**
> I edited my .vnc/xstartup.  Specifically remarking out /etc/X11/Xsession and adding the last 3 lines.


#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
#/etc/X11/Xsession

nautilus &
gnome-panel &
xterm &

Sephian that worked for me, finaly i can type again :). I'm a newbie and am trying to figure out what it did. Can you provide a little detail on what those 3 lines nautilus &,gnome-panel &, xterm & are doing? 
thanks!

---

