---
title: "beryl 0.1.1 restarting X server, 6.06"
date: 2006-11-15
forum: Desktop Environments
---

### Post by StarsAndBars14 on 2006-11-15
Got me a slight problem.

I tried upgrading to Beryl yesterday b/c I wanted some eye candy on my desktop. I'm using an EVGA e-GeForce 6200 AGP and I've put all the requisites into my xorg.conf file (ie TripleBuffer, RenderAccel and AllowARGBGLXVisuals) and I'm using the start method which involves making xgl.desktop in /usr/share/xsessions.

Every time I log in, to either GNOME or XGL, I see the Beryl splash screen after Ubuntu splash, and the server restarts in a couple of seconds.  I haven't had much luck combing through Xorg.0.log because all it gives me is "error opening /dev/wacom."

I've already upgraded the Xserver, gnome-session and libs to Quinn's, not to mention my gdm-conf.custom doesn't show anything out of whack so. . .what's going on here?  Is it an issue with my Beryl settings?

Help would be appreciated.

---

### Post by lamadredelsapo on 2007-01-04
Same problem here!!!! HELP!!!

---

### Post by muckz on 2007-02-04
I also have the same problem.

I installed Beryl, running Dapper Drake, nVidia Go 5200 card. At first, when I started Beryl, it redrew all my open windows, then didn't load. Followed some advice, turns out my depth was set to 16-bit. Set the depth to 24-bit, now whenever I load 'beryl-manager', my X server restarts.

Any clues, anybody? Please? Pretty please?

---

