---
title: "Lost my volume/sound indicator"
date: 2011-03-24
forum: Desktop Environments
---

### Post by dkruitz on 2011-03-24
I upgraded to Maverick things generally went well - but I noticed TWO sound controls and removed one - later after a reboot I no longer have any.  It will appear once I click on System/Preferences/Sound, but otherwise it doesn't show up on the desktop bar.  I checked under the Add to Panel feature but no luck - any ideas how to get it back?

---

### Post by Frogs Hair on 2011-03-24
Sound is included with the indicator applet on the add to panel menu.

---

### Post by 405jayb on 2011-03-24
Add this command to the start-up applications:
gnome-volume-control-applet

---

### Post by ps2k on 2011-05-14
I have similar issue. I had it before but after i re-installed alsa I lost it in 11.04. I could get a similar icon with "gnome-volume-control-applet" but is not the same one. I like the original icon.

---

### Post by Krytarik on 2011-05-14
ps2k, make sure that the package "indicator-sound" is installed (you may also reinstall it) and that "Indicator Applet" is added to your panel.

Greetings.

---

### Post by chev1n on 2011-05-29
I lost my volume indicator in 11.04. Installed indicator-sound, problem solved.

Thanks!!

---

