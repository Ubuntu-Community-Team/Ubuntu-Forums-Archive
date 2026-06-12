---
title: "[help] Still didn't work, desktop effects could not be enabled."
date: 2010-04-16
forum: Desktop Environments
---

### Post by kanaqsasak on 2010-04-16
Hello..
I'm using Dell Latitude C640
I've installed Ubuntu 9.10 Karmic Koala

I deleted my .gconf folder because of some messiness in my desktop after installing a game..

I have 2 user running on the same machine..
the other user can enable the desktop effects..
but mine still doesn't work, I think that is because I deleted the .gconf folder (CMIIW)

I've checked the compiz using compiz-check script, and it's fine..
here is the output:

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Could anyone give some help..? Thank you very much..

---

### Post by tom4everitt on 2010-04-16
I don't think deleting .gconf will brake compiz, if you look i'm pretty sure a new one has been created. 

But .gconf is not the only gnome-configuration folder. These also handle gnome settings:

.gconf
.gnome2_private
.gconfd
.gnome2
.config (i think)
.compiz (perhaps not gnome, but can also be relevant).

It might be idea to try deleting these also, hopefully resetting all gnome settings.

Otherwise the obvious solution is of course to create a new user, and delete malfunctioning one. If you're erasing most settings anyway, maybe its not such a big loss.

---

### Post by kanaqsasak on 2010-04-17
Thank you tom4everitt..
I think I can't create a new user because it will be a daunting task to start it all over again.. :)
I'll try to reset the setting first by deleting some of that folder you've listed..
Anyway, thanks..

---

