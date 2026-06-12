---
title: "Unity/Gnome not loading, Openbox fine"
date: 2015-04-25
forum: Desktop Environments
---

### Post by magnus7 on 2015-04-25
Hi,

I was running 15.04 pre-release and at one point unity stopped working. I don't recall messing with anything before it broke.

login is fine and uses my wallpaper.
Openbox and Kodi standalone works fine.
installed gnome and that is not working either.
If I autologin there is just a black screen.
With manual login I get just my wallpaper.
If i run "setsid unity" from terminal Unity starts, but doesn't load my full DE. E.g. the system bar on top is not populated but the launcher works.
The same goes for my guest account, so it is not just my user.

Intel Haswell graphics.

---

### Post by magnus7 on 2015-06-01
Time to bump this with some more info.

I installed kubuntu-desktop an that works too.

since it only seems to affect Unity and gnome I assume it has to do with "gnome-session".

when I select "upstart" instead of systemd from GRUB the option of starting an "Ubuntu" session is gone. I can only select the working kodi, Openbox, steamOS or Plasma sessions.

Any debugging advice appreciated...

---

### Post by Melodie on 2015-07-27
> **magnus7 said:**
> Time to bump this with some more info.

I installed kubuntu-desktop an that works too.

since it only seems to affect Unity and gnome I assume it has to do with "gnome-session".

when I select "upstart" instead of systemd from GRUB the option of starting an "Ubuntu" session is gone. I can only select the working kodi, Openbox, steamOS or Plasma sessions.

Any debugging advice appreciated...


Hello,

Are you still using the prerelease? Or did you reinstall fresh once the final has been out? Also upstart is about to be completely replaced by systemd. So, is your bug affecting the system only when you use upstart instead of systemd?

---

