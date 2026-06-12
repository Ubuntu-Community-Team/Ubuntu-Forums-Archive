---
title: "Windows in VNC are displaying garbled text"
date: 2008-11-20
forum: Desktop Environments
---

### Post by JimGvo on 2008-11-20
Configuration:  Compaq laptop running Ubuntu Hardy, tightvncserver Xvnc version 3.3.tight1.2.9

Started with vncserver -geometry 1000x700 :1

Attempting to access the laptop from another system running Ubunty Hardy, with:
xtightvncviewer                            1.2.9-22 

When I run the viewer (vncviewer 192.168.2.111:1)  I get the desktop with the xterm running as expected.  However when I type into any window that allows text input, it prints garbage.  I can't show it here since copy/paste doesn't work.

I do not have System/Preferences/Remote Desktop enabled on the laptop.

My .vnc/xstartup file looks like:
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

unset SESSION_MANAGER
gnome-session &


Any ideas?  

Also how do you get copy/paste to work from/to vnc?

Thanks,
Jim.

---

