---
title: "Login Loop except with Unity"
date: 2017-10-25
forum: Desktop Environments
---

### Post by prshah on 2017-10-25
Hello all,

I have been using and upgrading my Ubuntu for many years now.

I have recently updated from 17.04 to 17.10.

Since upgrading to 17.10, I am unable to log in with anything except Unity ; GNOME, GNOME with Xorg, Ubuntu, et all - all of them result in a login loop - except Unity, which works fine.

I am using lightdm - if I switch to GDM3, I don't get any greeter at all.

I checked relevant logs - /var/log/Xorg.?.log, /var/log/gdm3/ (blank directory) and .xsession-errors, nothings seems to jump out at me.

System config: AMD A6, 8Gb, Nvidia 9600 GT. Tech level - intermediate / high.

The same problem for all other users too.

I have the following DE's installed:
[list]
GNOME
GNOME Classic
GNOME on Xorg
IceWM Session
Ubuntu (Default)
Ubuntu on Xorg
Unity
[/list]

Of these - only IceWM and Unity work - all the rest give me a login loop.

Would appreciate any advice, troubleshooting or info gathering steps.

Regards,
PRS

---

