---
title: "Bluetile suddenly stopped starting..."
date: 2011-10-20
forum: Desktop Environments
---

### Post by deloquencia on 2011-10-20
Hello,


recently I faced an issue with Bluetile 0.5.1, Gnome 2.32.1 and gdm 2.32.1 at Ubuntu 11.04 (Natty). Bluetile suddenly didn't start anymore at login with gdm though all necessary configuration files have been in place and it started before without any problem.

First I tried to make bluetile starting with the default xsession configuration:

--- default /usr/share/xsessions/gnome-bluetile.desktop ---
```
[Desktop Entry]
Encoding=UTF-8
Name=GNOME + Bluetile
Comment=Tiling window manager
TryExec=/usr/bin/gnome-session
Exec=gnome-bluetile-session
Icon=bluetile.png
Type=XSession
```



It still doesn't started, so I tried again my own configuration which worked before.

--- modified /usr/share/xsessions/gnome-bluetile.desktop ---
```
[Desktop Entry]
Name=Bluetiled GNOME
Comment=Tiling window manager
Exec=/usr/bin/gnome-session --session=bluetile
TryExec=/usr/bin/gnome-session
Icon=bluetile.png
Type=(XSession and Application, I tried both)
```

--- /usr/share/gnome-session/sessions/bluetile.session ---
```
[GNOME Session]
Name=Bluetiled GNOME
Required=windowmanager;panel;filemanager;
Required-windowmanager=bluetile
Required-panel=gnome-panel
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
FallbackSessionsID=FallbackClassicGnome
FallbackClassicGnome=classic-gnome
```



So everything seems in place, but now it doesn't start anymore - even the fallback doesn't catch and starts default GNOME together with metacity. 

Which puzzles me most is that when I start bluetile manualy from a terminal it runs and takes place without any problem. I guess anything's wrong with it's configuration file. Also the .xsession-error.log doesn't show up some errors.

I'm stuck and puzzled. Do you have any idea where and how I could peek into it further? 

At the moment I solved the issue with a sloppy workaround. I'm using gnome-session-properties and starting bluetile like an application at startup.


Any help I'd appreciate, thanks for your time to scroll by :)
Thomas

---

