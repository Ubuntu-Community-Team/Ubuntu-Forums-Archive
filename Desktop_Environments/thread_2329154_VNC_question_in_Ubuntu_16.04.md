---
title: "VNC question in Ubuntu 16.04"
date: 2016-06-28
forum: Desktop Environments
---

### Post by Keith_Lynn on 2016-06-28
I have a new installation on Ubuntu 16.04 and have tightvncserver installed and it is working. Initially when I logged in with vnc (through ssh), I got just a grey screen. I checked online and there were some suggestions about what to do. Based on those suggestions, I changed ~/.vnc/xstartup to the following

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
# Fix to make GNOME work
#export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession

gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
gnome-session &

What I get now is a screen where I get a menu and start a terminal and so forth but it doesn't look anything like the screen I get if I login normally. Is there something else I need to start so I can see that in vnc? Thanks.

---

### Post by TheFu on 2016-06-30
Don't expect Unity or any DE that requred 3D video card accel to work through VNC. Use xfce or lxde or a straight window-manager solution instead.

BTW, the grey screen comes from the **xsetroot -solid grey** command.

I find **x2go** to be 2-3x faster than vnc-anything, but haven't moved to 16.04 on any servers. I know the x2go clients do work from a 16.04 system into a 14.04 system. x2go has the same limitation - no 3D accel DEs.

---

