---
title: "FVWM key bindings not working on remote VNC connection on Ubuntu 14.04.5 LTS"
date: 2016-12-14
forum: Desktop Environments
---

### Post by trivedia on 2016-12-14
On Ubuntu 12.04.5 LTS I had been successfully running FVWM on a VNC server (I have tried vnc4server and tightvncserver) and then accessing it remotely using a VNC viewer (I have tried xvnc4viewer and ssvnc). However, when I recently upgraded to Ubuntu 14.04.5 LTS, everything still works, but the key bindings on this remote FVWM session do not work (On a local, non-VNC FVWM session there is no such problem).


At this stage I am not sure where the problem lies, whether in Ubuntu 14.04.5 LTS or VNC server/client software, or something to do with FVWM or its configuration while running on a VNC server (see below for the two versions of ~/.vnc/xstartup that I have tried). However, other desktop environments that I tested, for example gnome-session and openbox, do not show such key binding problems. 


I would appreciate if someone could give me a solution or ideas for obtaining a solution.


~/.vnc/xstartup, version 1
--------------------------
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
fvwm2 &


~/.vnc/xstartup, version 2
--------------------------
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &


exec fvwm2

---

### Post by trivedia on 2016-12-14
[COLOR=#000000][FONT=&quot]So far the solution for me has been to install the FVWM version that worked with Ubuntu 12.04.5 LTS (Precise Pangolin), which is version 1:2.5.30.ds-1. This version works continues to work with Ubuntu 14.04.5 LTS (Trusty Tahr) (The FVWM version that came with Trust Tahr is 1:2.6.5.ds-3).[/FONT][/COLOR]

---

### Post by trivedia on 2016-12-14
To add more information for the original problem, I think it may already be encapsulated in the following bug report:
[https://bugs.launchpad.net/ubuntu/+source/fvwm/+bug/1333934](https://bugs.launchpad.net/ubuntu/+source/fvwm/+bug/1333934)

---

