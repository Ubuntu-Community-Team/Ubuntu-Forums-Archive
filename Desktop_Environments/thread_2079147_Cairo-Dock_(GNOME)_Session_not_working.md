---
title: "Cairo-Dock (GNOME) Session not working"
date: 2012-11-01
forum: Desktop Environments
---

### Post by samaresh on 2012-11-01
Cairo-Dock does not startup on login to Cairo-Dock (GNOME)  Session. But it's working fine from terminal.

Here is my ** /usr/share/xsessions/cairo-dock.desktop** configuration
```

[Desktop Entry]
Name=Cairo-Dock (GNOME)
Comment=This session logs you into GNOME with Cairo-Dock and with graphical effects.
Exec=gnome-session --session=cairo-dock
TryExec=cairo-dock-session
Icon=
Type=Application

```and **/usr/share/gnome-session/sessions/cairo-dock.session** configuration
```

[GNOME Session]
Name=Cairo-Dock Session
RequiredComponents=gnome-settings-daemon;
RequiredProviders=windowmanager;panel;
DefaultProvider-windowmanager=compiz
DefaultProvider-panel=cairo-dock
DesktopName=GNOME

```Please tell me what's going wrong .

---

