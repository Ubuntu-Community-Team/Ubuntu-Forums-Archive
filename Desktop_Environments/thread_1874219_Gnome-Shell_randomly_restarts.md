---
title: "Gnome-Shell randomly restarts"
date: 2011-11-02
forum: Desktop Environments
---

### Post by BazookaAce on 2011-11-02
Lately I've had some problems with Gnome-Shell 3.2. It restarts itself randomly (like when we do a ALT + F2 + R), and some times it doesn't bother to fully restart, so everything disappears and i'm left with the wallpaper, and i have to reboot the computer since it doesn't respond to CTRL + ALT + DEL (Log out).

Any ideas?

And one more thing. I'm also using XBMC (media center), and often when i fire it up it crashes completely and i get thrown out to the command prompt for about 5 seconds before i get logged out and LightDM loads up.

Again, any ideas?

Thanks in advance :)

---

### Post by nilarimogard on 2011-11-03
I don't know what's causing GNOME Shell to restart by itself, but when it doesn't fully restart, you can press CTRL + ALT + F1, log in and run these commands:
```
export DISPLAY=:0
gnome-shell --replace
```

Then press CTRL + ALT + F7 - this will take you back to GNOME Shell.

---

### Post by BazookaAce on 2011-11-03
That's the thing. I can't use my keyboard when it happens. The whole thing just shuts itself down.

---

### Post by victor9098 on 2011-12-02
The same thing happens to me! For no apparent reason, even when I am not in front of the computer, it does the same as the Alt+f2, then r command!

Going to look at filing a bug if nobody else has

---

### Post by victor9098 on 2011-12-02
OK, so I could not find a bug that exactly matches what we are both experiencing so I have filed [Bug #899491]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/899491"), please mark it as affecting you too if we have any hope of having anyone look at it!

---

