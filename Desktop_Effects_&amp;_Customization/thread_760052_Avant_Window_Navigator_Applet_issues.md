---
title: "Avant Window Navigator Applet issues"
date: 2008-04-19
forum: Desktop Effects &amp; Customization
---

### Post by Teamster on 2008-04-19
Hey folks, I got Avant Window Navigator installed, with the Manager, but I can't get any applets to work. I already have every conceivable dependency installed, but I simply can't get any other result than just the thin white lines that apparently represent the applets. Other threads seemed to want the readout of what happens in the terminal when it is launched:
```

art@art-laptop:~$ avant-window-navigator
Screen is composited.
LOADED : /usr/share/applications/firefox.desktop
LOADED : /home/art/.gnome2/panel2.d/default/launchers/Nautilus-1.desktop
LOADED : /usr/share/applications/gnome-terminal.desktop
LOADED : /usr/share/applications/ooo-writer.desktop
LOADED : /usr/share/applications/gnome-network-preferences.desktop
LOADED : /usr/share/applications/pidgin.desktop
APPLET : /usr/local/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/shinyswitcher.desktop
APPLET : /usr/lib/awn/applets/calendar.desktop
APPLET : /usr/lib/awn/applets/stacks.desktop
APPLET : /usr/lib/awn/applets/plugger.desktop

** (awn-applet-activation:6356): WARNING **: This desktop file does not exist /usr/lib/awn/applets/shinyswitcher.desktop


** (awn-applet-activation:6358): WARNING **: Unable to load module /usr/lib/awn/applets/calendar/clockcal.py


** (awn-applet-activation:6358): WARNING **: /usr/lib/awn/applets/calendar/clockcal.py: invalid ELF header

** (awn-applet-activation:6358): WARNING **: Could not create plug

APPLET : /usr/lib/awn/applets/weather.desktop

** (awn-applet-activation:6360): WARNING **: Unable to load module /usr/lib/awn/applets/stacks/stacks_applet.py


** (awn-applet-activation:6360): WARNING **: /usr/lib/awn/applets/stacks/stacks_applet.py: invalid ELF header

** (awn-applet-activation:6360): WARNING **: Could not create plug


** (awn-applet-activation:6362): WARNING **: This desktop file does not exist /usr/lib/awn/applets/plugger.desktop


** (awn-applet-activation:6364): WARNING **: Unable to load module /usr/lib/awn/applets/weather/weather.py


** (awn-applet-activation:6364): WARNING **: /usr/lib/awn/applets/weather/weather.py: invalid ELF header

** (awn-applet-activation:6364): WARNING **: Could not create plug


```
--

Any ideas?

---

### Post by moonbeam on 2008-04-19
> **Teamster said:**
> Hey folks, I got Avant Window Navigator installed, with the Manager, but I can't get any applets to work. I already have every conceivable dependency installed, but I simply can't get any other result than just the thin white lines that apparently represent the applets. Other threads seemed to want the readout of what happens in the terminal when it is launched:
--

Any ideas?

My suggestion.

1)  Remove all signs of awn from your system.  After removing it using synaptic make sure it is gone.  Specifically make sure there isn't a copy installed from source in /usr/local/*  (look for /usr/local/bin/avant-window-navigator )

2)  Install using the instructions at [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

---

### Post by Teamster on 2008-04-20
'Fraid it didn't work. Any other ideas?

And will this be fixed with 8.04?

---

### Post by kgr132 on 2008-04-21
Same problem here. Applets were working prior to a recent update. Now nothing. I guess I'll just wait and see if it works correctly in Hardy.

---

### Post by vaineh on 2008-04-22
same here, just white lines. has never worked for me.

---

### Post by Teamster on 2008-04-23
Well, I bit the bullet, and upgraded to the beta of Heron. Still, no banana. I can't get any applets to work, only white lines.

---

### Post by moonbeam on 2008-04-23
> **Teamster said:**
> Well, I bit the bullet, and upgraded to the beta of Heron. Still, no banana. I can't get any applets to work, only white lines.

If you haven't already it might be worthwhile to do a post on the awn forums [http://awn.planetblur.org](http://awn.planetblur.org).

The last few days there area variety of issues showing up with the Hardy packages in reacocard's repository, related to some build changes he made (which are actually appropriate for Hardy... but are getting a lot more testing now)

Beyond that if you post on the awn forums I would suggest giving system information and then run awn from a terminal and post the terminal output.

---

