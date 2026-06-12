---
title: "Unity dconf keys missing (Minimal install)"
date: 2013-01-26
forum: Desktop Environments
---

### Post by M4he on 2013-01-26
I just recently installed Ubuntu 12.10 from the [minimal CD image]("https://help.ubuntu.com/community/Installation/MinimalCD"), because I didn't want the bloat and decided to install everything from scratch.

I installed the unity desktop via
```
apt-get install --no-install-recommends ubuntu-desktop
```and manually added all the lenses and indicator packages.

However, some things are still missing. For example, the applet with the user name on it.
Here is how the panel looks right now: [http://postimage.org/image/552a164vr/](http://postimage.org/image/552a164vr/)

The second thing is, I wanted to whitelist a tray icon via dconf-key in "/desktop/unity/panel" but there seem to be a lot of dconf keys missing.
I neither have a section called "launcher" nor "panel" within the "/desktop/unity" dconf scheme.
The missing dconf keys could be related to the missing applet described above.

Any hints what package/command I could have missed?

Thanks!

---

