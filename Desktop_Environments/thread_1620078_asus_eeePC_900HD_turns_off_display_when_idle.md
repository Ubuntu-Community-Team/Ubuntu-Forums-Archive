---
title: "asus eeePC 900HD turns off display when idle"
date: 2010-11-12
forum: Desktop Environments
---

### Post by nsus on 2010-11-12
hello,

I've recently installed ubuntu 10.10 alongside windows vista as a  dual-boot on both of my computers.  This question pertains to my asus eeePC 900HD.  I'm quite new to ubuntu, so I'm sure I'll be needing a  lot of help.

I was having the problem of the computer freezing up when I unplugged it, but, thanks to these forums, I seem to have that fixed (gconf settings).
One similar problem remains.  After a minute or so of the computer being idle, the screen will fade to black, then, once the mouse is touched or a key pressed, the computer comes out of its idle state and prompts for a password.
I've opened  'gconf-editor'/apps/gnome-power-manager/ and in the /actions directors set the values of 'sleep_type_ac' and 'sleep_type_battery' to 'nothing'.  In /backlight I've switched the values of 'dpms_method_ac' and 'dpms_method_battery' to 'off'.  Also in /backlight I've switched the values of 'idle_dim_battery' and 'idle_dim_ac' to 'false', and just to be sure, set the 'idle_brightness' to 100% and the 'idle_dim_time' to 999.


Any ideas?

---

### Post by laurenbanjo on 2010-11-12
Did you try clicking on the battery icon and going into those preferences? You could also turn off the ask for password on return somewhere, I think.

---

