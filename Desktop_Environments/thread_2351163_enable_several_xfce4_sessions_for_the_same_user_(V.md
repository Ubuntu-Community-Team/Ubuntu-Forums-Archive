---
title: "enable several xfce4 sessions for the same user? (VNC)"
date: 2017-01-31
forum: Desktop Environments
---

### Post by kalyp on 2017-01-31
Hello,

Apologies if this has been answered elsewhere, in which case I haven't found it.
I am running a VNC server on a remote Xubuntu machine, and want to run a couple of them on my login (for instance one on :1, the other on :2). My xstartup ends with the line "startxfce4 &" and works perfectly when I start the first VNC session (eg., vnc4server :1).
However, any subsequent VNC session fails, connecting to it I only get a grey screen (+ terminal). It appears like startxfce4 fails because I can't have more than one at a time (??). Comparing the :1 and :2 vnc logs, :2 gives this error:
```
xfce4-session: Another session manager is already running
```

I don't remember having this issue before so not sure if something changed or I screwed up a setting somewhere, but any help would be much appreciated. (I have the same issue on Xubuntu 16.10 and Ubuntu 16.04).

Thanks in advance!

PS in case it is of use, my full xstartup:
```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
startxfce4 &

```

---

### Post by kalyp on 2017-01-31
Edit - I searched a bit more and found [https://bugzilla.xfce.org/show_bug.cgi?id=7502]("https://bugzilla.xfce.org/show_bug.cgi?id=7502")
While Alexis' workaround didn't work for me, using
```
env -u SESSION_MANAGER -u DBUS_SESSION_BUS_ADDRESS vncserver
```
did. So I guess this is solved. Hopefully this can save someone some time in the future!

---

