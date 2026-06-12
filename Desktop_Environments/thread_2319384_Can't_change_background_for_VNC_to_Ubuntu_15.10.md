---
title: "Can't change background for VNC to Ubuntu 15.10"
date: 2016-04-03
forum: Desktop Environments
---

### Post by rob-marshall17 on 2016-04-03
Hi,

I installed 15.10 desktop and vnc4server on a VM. When I initially created a VNC session I was able to set the background image and change it all I wanted. I then installed some more software and rebooted and now no matter what I do the background stays the same default gray/black dotted background that seems to waver obnoxiously. My .vnc/xstartup is:

```
#!/bin/sh


# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc


# [ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
# [ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
# xsetroot -solid grey
# vncconfig -iconic &
# x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# x-window-manager &


export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
 
gnome-session &
gnome-panel &
metacity &
gnome-settings-daemon &
gnome-terminal &

```

The background settings are currently:

```
rob@ubuntu-vm01:~/.vnc$ gsettings list-recursively org.gnome.desktop.background
org.gnome.desktop.background picture-opacity 100
org.gnome.desktop.background secondary-color '#5789ca'
org.gnome.desktop.background show-desktop-icons true
org.gnome.desktop.background primary-color '#023c88'
org.gnome.desktop.background color-shading-type 'solid'
org.gnome.desktop.background picture-options 'zoom'
org.gnome.desktop.background picture-uri 'file:///usr/share/backgrounds/Moss_inflorescence_by_carmelo75.jpg'
org.gnome.desktop.background draw-background true

```
Any suggestions? I keep trying different things to no avail.

Thanks,

Rob

---

