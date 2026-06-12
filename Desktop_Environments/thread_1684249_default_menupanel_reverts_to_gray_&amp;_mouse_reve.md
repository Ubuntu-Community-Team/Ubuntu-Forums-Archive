---
title: "default menu/panel reverts to gray &amp; mouse reverts 2 default"
date: 2011-02-08
forum: Desktop Environments
---

### Post by sevenenemy on 2011-02-08
ubuntu studio version of ultimate edition distro comes with all the crazy compiz stuff right off the bat. standard maverick distro base just a whole lotta repos and custom themes and other nifty things, if you got an extra dvd-r/w burn yourself a copy or make a usb and check it out its sick. this error also happened when i first started out with maverick so it could be happening due to hardware complications. compiz fusion icon wont open and panel/menus revert to ugly gray and i cant get it all to come back unless i goto system>>>preferences>>>apearance and then i can get it to reload. any ideas?

---

### Post by sevenenemy on 2011-02-08
in addition icons revert to default as well

---

### Post by Copper Bezel on 2011-02-08
This is coming up in every other thread these days - it affects Gnome Ubuntu distros after 10.04, but with unpredictable frequency. We've been seeing it a lot with netbooks, but it really seems quite random who gets it, how often....

The going fix is to add "gnome-settings-daemon" to your startup applications. It worked for me, but it hasn't worked for everyone.

To try it, next time you boot into default settings, run

gnome-settings-daemon && killall nautilus

It should fix everything immediately. This daemon is also launched (if it isn't running) by Appearance Preferences, so you've effectively been doing this. Restarting Nautilus is necessary because your desktop is rendered by Nautilus and won't update with everything else.

---

### Post by sevenenemy on 2011-02-09
yup its the gnome-settings-daemon that seems to fix this how do i make it permanent and load at boot?

---

### Post by Copper Bezel on 2011-02-09
In the main gnome menu, go to Preferences, then Startup Applications.

---

### Post by sevenenemy on 2011-02-09
so i got that all set up nice and easy, do i need to just killall nautilus after every boot? that would grind my gears. and while it did fix the icons/menus/panels all of compiz will not start load run however you wanna say it.

---

