---
title: "Meerkat - Removing 'New Wave' Crashes Appearance"
date: 2011-05-24
forum: Desktop Environments
---

### Post by sslemon on 2011-05-24
Let's get the technical out of the way:

 - virtualbox'd image, running on a x2 s939 + 4gib box + 7800gtx vidya

So, good thing is, I have a snapshot before the first graphical boot, but after the install. (Interrupted the reboot sequence :P) It's good, because now I don't have to continually reinstall Meerkat when I am slimming down the desktop installation.

The problem:  When I'm gksu'ing (gksu gnome-appearance-properties), I am removing unused theme components (Controls, Window Borders, Icons, et cetera), via the Remove/Delete buttons, et cetera. I've come from the top, worked my way from the bottom (both directions) and every time I remove 'New Wave' (I think there is another New Wave controls option for themeing), the Appearance applet closes. Can never reopen it.

I read through another thread on here about a similar situation, but they really didn't provide enough information about the 'crash' so I wanted to 'report' this, even if it's not a true bug.

So far, the resolution is to reload the snapshot (it's the root shell in the recovery mode phase between the first installation's first reboot before the login manager is loaded). It seems interesting that I cannot remove an unused theme (it will never be used, so why keep it) that the desktop is dependent on.

Which makes me want to wonder why so many things are dependent on others? I cannot remove the hicolor-icon-theme at all without totally removing gnome-desktop? Or maybe that's the real problem here. There isn't an abstracted theme hook that allows any theme to be installed; there's only the base theme and colors/icons/borders around it. Maybe that's not a problem at all, maybe it's just me. :confused:

---

### Post by Copper Bezel on 2011-05-24
Well, you don't really want to be running gnome-appearance-properties as root in the first place, as this also replaces Gnome's settings daemon with one running under root and could cause other problems. I imagine that the instability you're experiencing is a result.

If you'd like to remove unneeded themes, navigate to /usr/share/themes in a root Nautilus window (gksu nautilus) and remove the spares there.

---

