---
title: "Compiz-Fusion on KDE New Window Placement"
date: 2010-11-14
forum: Desktop Environments
---

### Post by armware on 2010-11-14
KDE: v4.5.1
Compiz: v0.8.6

When a new window is created it gets put into the lower right corner of the screen. Every window, every time, but only for the one user.

I have tried using options in the Place Window compiz plugin. The only thing that changed was if I disabled the plugin entirely, windows would be created way off screen, sometimes hidden on a different virtual desktop.
Changing the Placement Mode has no affect.

I eventually noticed that when apps are opened as root (via kdesudo), they are placed in the center of the screen.

I then tried to reset compiz settings to default via ccsm, all of my custom settings were gone but the issue at hand continues. I then switched to kwin, did a search in my home folder for all config files with compiz in the name (including hidden files) and removed them. I went back into compiz and the problem remained.

To clarify, I would prefer each app remembers its last position, though all I really want is for the small dialogs to quit appearing directly behind my vlc window, which I like to keep in the lower right corner, set to always on top and to all desktops.

---

### Post by armware on 2010-12-19
for what it's worth:

removed and purged all compiz packages and reset everything to use kwin, then reinstalled packages one at a time.

---

