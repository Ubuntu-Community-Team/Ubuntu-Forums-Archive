---
title: "Prevent Display/Computer from sleep"
date: 2012-04-10
forum: Desktop Environments
---

### Post by Lumio on 2012-04-10
Hi,

I just installed Xubuntu and configured lightdm (/etc/lightdm/lightdm.conf) as the following to have an auto-login:
```
[SeatDefaults]
user-session=xubuntu
greeter-session=lightdm-gtk-greeter
autologin-user=lumio
autologin-user-timeout=0
```

After login chromium-browser is executed in kiosk-mode, calling localhost...

I set the power management to prevent the computer from sleep, but anyhow - after a few minutes it falls asleep.

The even worse thing about that: I can't use X anylonger after I wake my computer up. I can use the mouse, but ending in a sort of raw-console where any key-press is displayed in raw.

Does anyone know how to prevent the computer from falling asleep?

Thanks :)

---

### Post by kiirokurisu on 2012-04-11
Have you verified that in the computer's BIOS no sleep times are configured?

---

