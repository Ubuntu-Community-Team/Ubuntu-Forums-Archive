---
title: "Unity Launcher in GNOME classic after enabling Compiz"
date: 2011-11-19
forum: Desktop Environments
---

### Post by teh5abiking on 2011-11-19
So I've had my fill of Unity, just as much as everyone else, but I decided to stick with GNOME Classic. 

However several issues, I've incurred: 

- After enabling Compiz in GNOME classic, the Volume and WiFi icons disappear from the top panel
- After logging out and logging back into the classic session, the Unity launcher appears, and that kinda ruins the GNOME classic experience for me, because well I wanted to get away from Unity. 

Here's a copy of my gnome-classic.session file. 

```
[GNOME Session]
Name=GNOME Classic
RequiredComponents=gnome-panel;gnome-settings-daemon;
RequiredProviders=windowmanager;
DefaultProvider-windowmanager=gnome-wm
DefaultProvider-notifications=notify-osd
IsRunnableHelper=/usr/lib/gnome-session/gnome-session-check-accelerated
FallbackSession=gnome-fallback
DesktopName=GNOME

```

Is there anything that I can do?

---

### Post by Larkspur on 2011-11-19
Check ccsm to see if the Unity plugin is still ticked.  I think it will be by default with compiz.

---

### Post by teh5abiking on 2011-11-19
thanks, as it turns out, i edited the wrong file. 

it was supposed to be gnome-fallback.session, and i edited the wrong element as well. 

all is right. 

i also checked ccsm, and the unity plugin was still enabled.

---

