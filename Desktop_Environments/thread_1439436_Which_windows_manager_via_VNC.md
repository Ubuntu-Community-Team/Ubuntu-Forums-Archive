---
title: "Which windows manager via VNC?"
date: 2010-03-26
forum: Desktop Environments
---

### Post by dizzle118 on 2010-03-26
I want to replicate GNOME as close as possible when I VNC to my Ubuntu 9.10 box, within vncserver /.vnc/xstartup I have the following defined:

> #!/bin/sh

# Uncomment the following two lines for normal desktop:
#unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &
gnome-session &I installed twm, its ok but I would like a like-for-like session as if I were at the console, if I comment out twm, it looks the same but I can move or resize windows.  I'd like to hear from you guys n gals to what windows manager is best or am I simply missing something ?

thanks ;)

---

### Post by at165db on 2010-03-26
VNC is so awful.  Way too much lag, and try using it over DSL/Cable via VPN.

You should check out NX.  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

It lets you log in to your desktop environment as a separate session, and everything "just works".  It uses something like compressed X server message tunneling for crazy responsiveness, and you don't have all the mouse cursor lag.  NX is also nice because more than one user (diff accounts) can log into the same machine, and have separate sessions.

---

### Post by dizzle118 on 2010-03-29
have you full control from poweron ?  ie from Logon screen?

---

### Post by nickbnf on 2010-03-29
I found fluxbox to be a good middle ground between full fledged gnome/kde and twm over VNC.

My .vnc/xstartup:
```

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
rxvt -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
/usr/bin/startfluxbox

```

It runs ok-ish over my connection but I have to give NX a try.

---

