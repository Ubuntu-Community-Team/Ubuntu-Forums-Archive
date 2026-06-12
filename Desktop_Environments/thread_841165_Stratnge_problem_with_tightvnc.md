---
title: "Stratnge problem with tightvnc"
date: 2008-06-26
forum: Desktop Environments
---

### Post by vmeli on 2008-06-26
I'm using Kubuntu 8.04 and I have installed tightvnc. My xstartup is the following

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc
startkde &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &


Everything is running ok except one thing. Everytime I try to run something that needs sudo password , like synaptics or administrator mode in system settings, it accepts the password but nothing is opening. If I run in console "sudo synaptics" I give the password and it opens. Any ideas?

---

### Post by vmeli on 2008-06-28
Anyone?

---

### Post by teamloser on 2008-07-22
I have the same issue.

---

