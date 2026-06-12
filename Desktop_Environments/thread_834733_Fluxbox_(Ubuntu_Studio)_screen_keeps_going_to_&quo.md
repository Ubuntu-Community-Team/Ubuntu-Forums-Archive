---
title: "Fluxbox (Ubuntu Studio): screen keeps going to &quot;sleep&quot; despite my settings"
date: 2008-06-19
forum: Desktop Environments
---

### Post by T4_ on 2008-06-19
Hi all,

In gnome-power-preferences I've got it set that the screen should never, ever turn itself off/go to sleep after a certain amount of time. However, in Fluxbox it still does it.

I'm trying to enjoy Chaplin's "The Circus" but every ten minutes I have to move the mouse about. Quite annoying :p

It makes no difference whether gnome-power-manager is running or not.

I added "xset s off" to Fluxbox's startup file but to no avail.

Does anyone have any ideas?


[edit]
SOLVED - see replies.

---

### Post by p_quarles on 2008-06-20
How are you initializing Fluxbox? Really, gnome-power-preferences shouldn't even be running unless you tell it to. I imagine that this is a background daemon. The results of the following command might be helpful in diagnosing this:
```
ls /etc/rc2.d
```

---

### Post by kerry_s on 2008-06-20
```
xset -dpms
```

---

### Post by T4_ on 2008-06-20
Thanks for the replies.

I think Gnome's power settings started to run after I ran the "Appearance" settings to change the colour of the windows (not the borders etc, but the background of toolbars, statusbar etc) whilst logged in with Fluxbox as Window Manager. The fact that I initialised the power settings GUI after that, to check the settings, didn't help either - not to mention that I tried to start gnome-screensaver; xterm didn't inform me that the command did not exist, the GUI just did not appear... so whilst trying to fix this issue, I may in fact have made it worse - ah well, my teachers all those years ago were right: indeed not a day goes by without learning something :)

The DPMS settings didn't change a thing, unfortunately. However, after exhausting the googled options I logged into Gnome and found the screensaver settings... Just watched "Mr Verdoux" without problems :) (Might as well throw in some good-movie-advice with my questions! ;))

It's amazing how sometimes all these different settings can override eachother.

So yeah, after editing Fluxbox's startup/init file, trying "temporary" settings in the terminal ("xset -dpms & xset s off"), and editing xorg.conf; this problem was solved by simply unchecking a box in Gnome's screensaver settings - which, as I don't use a screensaver, I had not included in my manually-typed Fluxbox menu.

The simplest things are always the easiest to overlook :oops:

---

