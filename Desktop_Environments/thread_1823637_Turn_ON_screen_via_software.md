---
title: "Turn ON screen via software"
date: 2011-08-12
forum: Desktop Environments
---

### Post by gatewayasteroid on 2011-08-12
I need to turn ON my screen after I got an incoming call through Skype. My speakers are built-in and if the screen is off they can't make any sound. I know I just have to add a custom command in the skype incoming call advanced settings.

Note: doing it in a non Gnome system is trivial with *xset*, that's what I'm doing now. But I would like to know whether it's possible in Gnome/Unity.

Thanks

---

### Post by gatewayasteroid on 2011-08-13
> **gatewayasteroid said:**
> I need to turn ON my screen after I got an incoming call through Skype. My speakers are built-in and if the screen is off they can't make any sound. I know I just have to add a custom command in the skype incoming call advanced settings.

Note: doing it in a non Gnome system is trivial with *xset*, that's what I'm doing now. But I would like to know whether it's possible in Gnome/Unity.

Thanks

A workaround is to set gnome power manager to never turn off the display, and start "xset dpms X Y Z" at startup.

---

