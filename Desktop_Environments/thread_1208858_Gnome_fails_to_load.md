---
title: "Gnome fails to load"
date: 2009-07-09
forum: Desktop Environments
---

### Post by Intrepid Ibex on 2009-07-09
When I start up my GNOME, nothing loads up! I can only move my mouse in front of the background.

What is this?

---

### Post by Intrepid Ibex on 2009-07-10
Right clicking the desktop won't work, alt+f2 won't work, icons aren't showing up, reinstalling hal won't work, inputting cd won't work, "Ctrl+c" won't work, using "nv" driver won't work, gnome failsafe mode won't work, nothing will!

The first time I had this issue I could see my icons and could right click the desktop and create a launcher for terminal and I could just start gnome panel.

Then I moved my .gnome2 and .gnome2_private from home and now I'm at this point.

BUMP!

---

### Post by wojox on 2009-07-10
Drop into a shell on boot and type:

```
dpkg --configure -a
```

then exit/restart

---

### Post by Intrepid Ibex on 2009-07-10
Sorry I forgot to mention that I'm using arch linux and my packages aren't corrupt. I believe some settings file is.

**Edit:** When launching ```
gnome-session
``` manually, I get a pop-up: ```
Could not acquire name on session bus
``` and terminal says: ```
[det@myhost ~]$ gnome-session
gnome-session[4552]: WARNING: Could not parse desktop file /home/det/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
gnome-session[4552]: WARNING: could not read /home/det/.config/autostart/xfconf-migration-4.6.desktop
GNOME_KEYRING_SOCKET=/tmp/keyring-32mWEY/socket
SSH_AUTH_SOCK=/tmp/keyring-32mWEY/socket.ssh

** (gnome-settings-daemon:4559): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:4559): WARNING **: Could not acquire name

MCS->Xfconf settings migration complete

  

```

---

