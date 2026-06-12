---
title: "Disable Screen Saver turning off of monitor"
date: 2010-07-04
forum: Desktop Environments
---

### Post by Vaxon on 2010-07-04
after 10 minutes my screen while go blank
was wondering how to turn it off
using kubuntu 10.04

---

### Post by hictio on 2010-07-04
If it helps, on Gnome, is on the "Power Management", for both of the options, turning the monitor off after X amount of minutes, or not doing so never.

---

### Post by Vaxon on 2010-07-04
Thank you for the quick response but sadly things are not the same in kde

---

### Post by ankspo71 on 2010-07-05
Hi,
For screensaver and lockscreen options:
Go to Settings > System Settings > Desktop > Screensaver
You can turn off the screensaver here, and also disable the password lock for the screensvaer.

For power management:
Go to Settings > System Settings > Advanced (tab) > Power Management.
There's a few options in here, but I think to disable it you just uncheck:
"Lock screen on resume" and "Let PowerDevil manage screen powersaving"
then click apply.
Hope that helps.

---

### Post by jbo5112 on 2010-07-05
I don't think you need to uncheck "Lock screen on resume".  I think that has to do with a suspend to RAM or disk, but I could be wrong.  Also, if you click on edit profiles from that screen, there is a screen tab that lets you adjust the time for each level of powersave on your monitor for each power profile.

There is another option.  This only turns it off until you log out, but you can type "xset -dpms" (without quotes) in a terminal window or in the run command window.  Typing "xset +dpms" turns it back on.  I have "Lock screen on resume"custom ModeLines set up to squeeze a few more Hz out of the video bandwidth to my CRT, so I just manage my powersave setting in my xorg.conf.

---

### Post by skywatcher55 on 2011-06-03
well mine dont have the "turn off screen saver" or disable password ability. Shucks.

---

### Post by DewS on 2011-07-28
Damn, now i also have this issue.
Must be a recent update or something, because it always worked before (using lucid)

Screen actually shuts down, not just a 'blank screen' every 10 min.

---

