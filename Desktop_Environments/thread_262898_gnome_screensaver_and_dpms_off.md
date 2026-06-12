---
title: "gnome screensaver and dpms off"
date: 2006-09-22
forum: Desktop Environments
---

### Post by SCSIMouse on 2006-09-22
The laptop lid switch is broken on my laptop (Dell Inspiron 1100) and when I close the lid the screen doesn't shut off.  This wouldn't be so much of a problem if the gnome screensaver would turn off the backlight for me.  It doesn't for some reason.  Does anyone know of some way I could change/make my own little screensaver for gnome that would just do dpms off and on?

---

### Post by wkulecz on 2006-09-22
My Ubuntu system has been very stable, but I enabled the screen saver just for grins, and my box was locked up when I returned this morning.  Its ran for over a week without the screen saver enabled.  Not sure what to make of this, no UPS for this system yet so it could have been a powerline problem or an issue with a specific screensaver.

In use, I need the display to be always visible unless I turn it off, so I disabled the screensaver and added these to xorg.conf file:

Section "ServerFlags"
	Option "StandByTime"	"0"
	Option "SuspendTime"	"0"
	Option "OffTime"	"0"
EndSection

But the screen still blanked after a time interval with no mouse or keyboard activity.  Going to "System->Preferences->power management"  I found a "put monitor to sleep if inactive for" slider which I set to never and now no blanking.

Sounds to me that adding the server flags and setting the slider to whatever blanking interval you want should do the trick.

HTH,
--wally.

---

