---
title: "Gnome desktop on xubuntu"
date: 2010-04-22
forum: Desktop Environments
---

### Post by ubunterooster on 2010-04-22
I was messing around logged out of gnome and into xcfe and I saw my gnome background. Which was odd but not disturbing until I right-clicked and got gnome's desktop menu.

So I have no right-click to bring up my application menu; it drives me nuts!

---

### Post by Brandon Williams on 2010-04-23
That sounds like nautilus is running. Do you have a listing for nautilus under Sessions and Startup -> Autostarted Applications ? If so, you may need to add 'NotShowIn=XFCE;' to the associated .desktop file in your ~/.config/autostart/ folder.

---

### Post by ubunterooster on 2010-04-23
gnome-settings-deamon.desktop?
```
[Desktop Entry]
X-Ubuntu-Gettext-Domain=gnome-settings-daemon
Name=GNOME Settings Daemon
X-GNOME-Autostart-Notify=true
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
X-GNOME-Autostart-Phase=Initialization
OnlyShowIn=GNOME;
Type=Application
X-GNOME-AutoRestart=true
X-GNOME-Autostart-enabled=false 
```

---

### Post by Brandon Williams on 2010-04-23
That's marked "OnlyShowIn=GNOME;", so that won't be it. You may need to check /etc/xdg/autostart/, too, since the things there will be autostarted unless you override them in your own ~/.config/autostart/.

First, though, make sure that I'm right about nautilus running. What does 'ps -ef | grep nautilus' say?

---

### Post by ubunterooster on 2010-04-23
ps -ef | grep nautilus
josiah   11104 11049  1 22:03 ?        00:00:01 nautilus --sm-client-id 25f52597d-11fe-4a44-a747-16369191f4e1 --sm-client-state-file /home/josiah/.config/session-state/nautilus-1272043418.desktop
josiah   11276 11198  0 22:05 pts/0    00:00:00 grep --color=auto nautilus

---

### Post by ubunterooster on 2010-04-24
Gnome-settings-daemon.desktop in /etc/xdg/autostart
```
[Desktop Entry]
Type=Application
Name=GNOME Settings Daemon
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
OnlyShowIn=GNOME;
X-GNOME-Autostart-Phase=Initialization
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=gnome-settings-daemon
```

The desktop is fine in LXDE, E16, KDE, Fluxbox... Just xcfe has the problem.

---

### Post by ubunterooster on 2010-04-24
It was nautilus:
 I found that folders on the desktop are opened by nautilus but folders accessed via the xcfe places menu are opened by Thunar. So I removed nautilus, logged out and logged back in. The background is now the blue trees (same as splash). Oh, and no icons or options on right-click at all. So I reinstalled Nautilus and redid logout/login. Still shows splash image.

    Coming from no panels and everything on my xcfe desktop a few months ago, this will take a lot of getting used to.

---

### Post by ubunterooster on 2010-04-24
I went to the xcfe settings panel>startup. Yep, that was the problem. :D Thanks for pointing me in the right direction, Brandon. :)

---

