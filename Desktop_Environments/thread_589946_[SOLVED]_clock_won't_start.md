---
title: "[SOLVED] clock won't start"
date: 2007-10-24
forum: Desktop Environments
---

### Post by duffrecords on 2007-10-24
After I upgraded to Gutsy, GNOME's clock disappeared.  I get the following error message:> The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".
Do you want to delete the applet from your configuration?I had some other trouble with Evolution not finding shared object files, so I'm wondering if this is somehow related, since Evolution and the clock/calendar integrate together.  Someone in an older post recommended running clock-applet but it doesn't appear to exist on my system.  I can't find it in Synaptic Package Manager either, although I did uninstall/reinstall gnome-applets.  How do I reinstall the clock?

---

### Post by duffrecords on 2007-10-26
A little more information on the problem... I realized the clock is part of gnome-panel, not gnome-applets.  I uninstalled and reinstalled that to no avail.  All the other panel applets can be added, but not the clock.

---

### Post by duffrecords on 2007-10-29
I now have a very strong suspicion this clock problem is associated with Evolution.  I just discovered I can't add new contacts or calendar appointments.  When I click "new contact" nothing happens.  When I click "new appointment" it says "There is no calendar available for creating events and meetings."  I've completely removed and reinstalled the following packages:
[LIST]
[*]evolution
[*]evolution-common
[*]evolution-data-server
[*]evolution-data-server-common
[*]evolution-exchange
[*]evolution-plugins
[*]evolution-webcal
[*]gnome-panel
[*]gnome-panel-data
[*]gnome-applets
[*]gnome-applets-data
[/LIST]
But the problems still persist.  I searched my filesystem for broken symlinks but I don't see any that pertain to these packages.  Can anyone suggest some other troubleshooting steps?

---

### Post by duffrecords on 2007-11-05
Ok, this issue has gone too far.  My Gutsy upgrade seems to have a degenerative condition because something new breaks every day.  Now the trash and battery applets can't be loaded into gnome-panel, my screen resolution changes after coming back from the screen saver or when logging back in, and after a few hours of use the content of programs and windows goes black while the window decoration and desktop stay normal.

I've read some posts advising against using the network upgrade, so I'm going to try a clean install from a CD this time and if that doesn't work I'm going back to Feisty.  I hope it works, because the main reason I upgraded was so I could get Evolution 2.12 with the bogofilter plugin (which gave me trouble compiling from source).

---

### Post by duffrecords on 2007-11-10
Installing 7.10 from the CD fixed everything, although it may be too early to say that with confidence.  My advice--don't use the network upgrade.

---

