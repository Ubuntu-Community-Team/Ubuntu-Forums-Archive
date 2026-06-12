---
title: "Panel &amp; menu disapeared from remote desktop"
date: 2019-11-08
forum: Desktop Environments
---

### Post by makem2 on 2019-11-08
I have just setup Ubuntu 19.10 on a Raspberry Pi4 and am using tightvnc from a linux laptop to access it remotely, headless. When first started it had a top panel with menu etc.

Whilst investigating how to set up wifi access the panel disappeared from under my mouse!

The Remote setup is:

vncserver@.service

```

[Unit]
 Description=Remote desktop service (VNC)
 After=syslog.target network.target

[Service]
  Type=forking
  User=makem
  PIDFile=/home/makem/.vnc/%H:%i.pid
  ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
  ExecStart=/usr/bin/vncserver -depth 24 -geometry 1920x1080 :%i
  ExecStop=/usr/bin/vncserver -kill :%i

[Install]
  WantedBy=multi-user.target

```

xstartup

```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
#unset DBUS_SESSION_BUS_ADDRESS
#exec /etc/X11/xinit/xinitrc
#/usr/bin/mate-session &


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
#export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession
startxfce4 &

```

The server is working correctly:

```

makem@ubuntu:~/.vnc$ sudo systemctl status vncserver@1 -l
&#9679; vncserver@1.service - Remote desktop service (VNC)
   Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2019-11-08 19:36:37 UTC; 34min ago
  Process: 1258 ExecStartPre=/usr/bin/vncserver -kill :1 > /dev/null 2>&1 (code=exited, status=0/SUCCESS)
  Process: 1285 ExecStart=/usr/bin/vncserver -depth 24 -geometry 1920x1080 :1 (code=exited, status=0/SUCCESS)
 Main PID: 1296 (Xtightvnc)
    Tasks: 96 (limit: 4206)
   CGroup: /system.slice/system-vncserver.slice/vncserver@1.service
           &#9500;&#9472;1296 Xtightvnc :1 -desktop X -auth /home/makem/.Xauthority -geometry 1920x1080 -depth 24 -rfbwait 120000 -rf
           &#9500;&#9472;1367 xfce4-session
           &#9500;&#9472;1465 /usr/bin/dbus-launch --sh-syntax --exit-with-session xfce4-session
           &#9500;&#9472;1474 /usr/bin/dbus-daemon --syslog --fork --print-pid 5 --print-address 7 --session
           &#9500;&#9472;1485 /usr/lib/at-spi2-core/at-spi-bus-launcher
           &#9500;&#9472;1491 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-addr
           &#9500;&#9472;1495 /usr/lib/aarch64-linux-gnu/xfce4/xfconf/xfconfd
           &#9500;&#9472;1501 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
           &#9500;&#9472;1505 /usr/bin/gnome-screensaver --no-daemon
           &#9500;&#9472;1513 /usr/lib/gvfs/gvfsd
           &#9500;&#9472;1522 /usr/bin/ssh-agent -s
           &#9500;&#9472;1525 /usr/bin/gpg-agent --sh --daemon --write-env-file /home/makem/.cache/gpg-agent-info
           &#9500;&#9472;1526 xfwm4
           &#9500;&#9472;1540 xfsettingsd
           &#9500;&#9472;1557 Thunar --daemon
           &#9500;&#9472;1562 xfdesktop
           &#9500;&#9472;1590 /usr/libexec/evolution-data-server/evolution-alarm-notify
           &#9500;&#9472;1591 /usr/lib/geoclue-2.0/demos/agent
           &#9500;&#9472;1594 /usr/bin/python3 /usr/share/system-config-printer/applet.py
           &#9500;&#9472;1606 /usr/lib/dconf/dconf-service
           &#9500;&#9472;1610 xiccd
           &#9500;&#9472;1612 xfce4-power-manager
           &#9500;&#9472;1652 /usr/lib/aarch64-linux-gnu/xfce4/notifyd/xfce4-notifyd
           &#9500;&#9472;1666 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
           &#9500;&#9472;1703 /usr/lib/gvfs/gvfsd-trash --spawner :1.7 /org/gtk/gvfs/exec_spaw/0
           &#9500;&#9472;1719 /usr/libexec/evolution-source-registry
           &#9500;&#9472;1721 /usr/lib/gvfs/gvfsd-metadata
           &#9500;&#9472;1733 /usr/lib/gnome-online-accounts/goa-daemon
           &#9500;&#9472;1740 /usr/lib/gnome-online-accounts/goa-identity-service
           &#9500;&#9472;1761 /usr/libexec/evolution-calendar-factory
           &#9492;&#9472;1776 /usr/libexec/evolution-addressbook-factory

Nov 08 19:36:46 ubuntu dbus-daemon[1474]: [session uid=1001 pid=1464] Successfully activated service 'org.gnome.OnlineAcc
Nov 08 19:36:46 ubuntu dbus-daemon[1474]: [session uid=1001 pid=1464] Successfully activated service 'org.gnome.Identity'
Nov 08 19:36:46 ubuntu dbus-daemon[1474]: [session uid=1001 pid=1464] Activating service name='org.gnome.evolution.datase
Nov 08 19:36:47 ubuntu dbus-daemon[1474]: [session uid=1001 pid=1464] Successfully activated service 'org.gnome.evolution
Nov 08 19:36:47 ubuntu dbus-daemon[1474]: [session uid=1001 pid=1464] Activating service name='org.gnome.evolution.datase
Nov 08 19:36:47 ubuntu dbus-daemon[1474]: [session uid=1001 pid=1464] Successfully activated service 'org.gnome.evolution
Nov 08 19:44:28 ubuntu dbus-daemon[1474]: [session uid=1001 pid=1464] Activating service name='org.freedesktop.thumbnails
Nov 08 19:44:28 ubuntu org.freedesktop.thumbnails.Thumbnailer1[1474]: Registered thumbnailer /usr/bin/gdk-pixbuf-thumbnai
Nov 08 19:44:28 ubuntu org.freedesktop.thumbnails.Thumbnailer1[1474]: Registered thumbnailer /usr/bin/gdk-pixbuf-thumbnai
Nov 08 19:44:28 ubuntu dbus-daemon[1474]: [session uid=1001 pid=1464] Successfully activated service 'org.freedesktop.thu
makem@ubuntu:~/.vnc$ 

```

Edit: I experimented with geometry and depth settings and the panel returned but the screen is reduced in size and when full sreen has black borders all around.

The setting I tried were:

1. depth 32 geometry 1920x1080
2. depth 32 geometry 1600×900
3. depth 24 geometry 1920x1080
4. depth 24 geometry 1600×900

So, partially solved and at least I can now find about restoring wifi use (All settings greyed out) while hopefully someone can help with the fullscreen problem (Should I change the title?)

---

