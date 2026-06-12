---
title: "Get vncserver to display my current XFCE desktop"
date: 2008-04-08
forum: Desktop Environments
---

### Post by boondocks on 2008-04-08
I am running XFCE on Xubuntu system whose ip address is 192.168.3.171

My "~/.vnc/xstartup" contains:
```
# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &
```I did a "vncserver :1" at the XFCE desktop.

Then from a nearby Windows XP, I pointed a vncviewer to 192.168.3.171:1
This gives me just a blank desktop on 192.168.3.171
Please see the attached "Blank_Desktop.gif"

So how do I get (the vncserver to display) my current XFCE desktop ?

---

### Post by Mithrilhall on 2008-04-08
Try x11vnc

x11vnc allows one to view remotely and interact with real X displays (i.e. a display corresponding to a physical monitor, keyboard, and mouse) with any VNC viewer. In this way it plays the role for Unix/X11 that WinVNC plays for Windows.

[http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

It's in the repos.

---

### Post by boondocks on 2008-04-08
Great.  Thanks.  That helped.

---

### Post by .nedberg on 2008-04-08
You could also try vino, also in the repos

---

