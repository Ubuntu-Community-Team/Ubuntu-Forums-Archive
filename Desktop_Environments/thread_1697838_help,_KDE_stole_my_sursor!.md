---
title: "help, KDE stole my sursor!"
date: 2011-03-01
forum: Desktop Environments
---

### Post by eanema on 2011-03-01
Hi All,

I've been running Ubuntu/Gnome for quite some time now. A while ago I wanted to try out KDE so I installed the KDE package. I quickly decided that I didn't like it so I switched back to running Gnome. The problem is that KDE has stolen my mouse cursor. Now, in Gnome, I am stuck using the wimpy round grey arrow and the two twirling balls instead of an hour glass. I have tried changing the  pointer in the Preferences=>Appearance app, but it keeps coming back.

Any Thoughts?

---

### Post by Zorael on 2011-03-01
It's not wimpy! :3 But they are twirling.

You can change the default cursor by running the following in a terminal and picking the GNOME one. Human? something like that.
```
$ sudo update-alternatives --config x-cursor-theme
```

You can also remove the Oxygen cursor theme package entirely. Its name is, not too surprisingly, **oxygen-cursor-theme**.

---

