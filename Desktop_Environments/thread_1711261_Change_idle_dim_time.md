---
title: "Change idle dim time"
date: 2011-03-21
forum: Desktop Environments
---

### Post by kcxzero on 2011-03-21
Anyone have an alternative to gconf-editor for changing the idle dim time? I have a Vaio, which hasn't exactly been compatible with ubuntu but I've been making it work.

What I'm looking for is an alternative, like the the one I'm using to control the back light (nvclock). If anyone knows of a method, please let me know.

Sony Vaio VGN-SZ750N
Ubuntu 10.10
Nvidia 8400M GS

---

### Post by MunkyBite on 2011-06-02
I'm on 11.04 on Viao VGN-NR110E and used following in the terminal:

```
gconftool --type int --set /apps/gnome-power-manager/backlight/idle_dim_time 120
```Where 120 is the seconds until dim. I pulled it from this thread:

[http://ubuntuforums.org/showthread.php?t=1024735&highlight=changing+the+dim+display+idle+time](http://ubuntuforums.org/showthread.php?t=1024735&highlight=changing+the+dim+display+idle+time)

---

### Post by Copper Bezel on 2011-06-02
Whether you're using gconf-editor or gconftool2, you're changing the same setting in gconf, which corresponds to (and can be set in) Gnome Power Manager, which you can get to by clicking the battery icon in the system tray and selecting Settings from the menu.

What problem are you having, however, with this setting? Is Gnome Power Manager not behaving as you set?

---

### Post by ravenpi on 2013-05-01
Yeah... not so much.  The setting they -- and I -- are looking for (I think) is one where, when the system is on battery, AND "dim screen when idle" is checked, you could alter the timeout before dimming.  It seems to be about 30 seconds, which is simply too short to (say) read a paragraph of text before scrolling.  So you're constantly going back and forth with dimming.  Sub-optimal.  And there's no setting for the actual timeout in the power control panel.  There *IS* the option to put the screen to sleep after a given amount of time, but that's not quite the same thing.

---

