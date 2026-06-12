---
title: "gnome-screensaver locked up, killed, can't restart?"
date: 2007-05-21
forum: Desktop Environments
---

### Post by ender42 on 2007-05-21
So, I used the Gnome panel to add lock screen, which runs a screen-saver and locks my screen when I'm away from my computer.  But it had locked up, and wouldn't respond to mouse or keyboard when I wanted to log back in.  I swapped to tty1, logged in, and killed 'gnome-screensaver' which got me back my GUI.

Cool so far.

Tried to lock my screen when I had to leave, no dice - becasue the program hasn't restarted.  Tried restarting it in tty1, got an error:

```

(gnome-screensaver:30128): gnome-screensaver-WARNING **: cannot open display (null)

```

Tried starting it up from System:Preferences:Screensaver Preferences panel, no dice.

So, how do I get this restarted without rebooting?

---

