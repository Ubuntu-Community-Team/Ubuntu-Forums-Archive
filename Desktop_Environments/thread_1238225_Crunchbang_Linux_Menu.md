---
title: "Crunchbang Linux Menu"
date: 2009-08-12
forum: Desktop Environments
---

### Post by andygee on 2009-08-12
I'm trying for a really simple desktop and, have searched for hours to find the menu program they use in crunchbang linux. It looks like a right chick job with the applications, places and system, coming from the click of the mouse. also is there away to have no panels?

---

### Post by Dark Hornet on 2009-08-12
Crunchbang is a great project...I have it running on an old PC of mine.  It uses Openbox as the window manager, and as you have found you will need to right click to find your apps, etc.  Take a look at these two links for tips and help on configuring Openbox, and let me know if you have any additional questions....

Darkhornet

[http://ubuntuforums.org/showthread.php?t=192106](http://ubuntuforums.org/showthread.php?t=192106)

[http://icculus.org/openbox/index.php/Help:Contents](http://icculus.org/openbox/index.php/Help:Contents)

---

### Post by snowpine on 2009-08-12
Hi Andy, you can edit the menus in Crunchbang (#!) in a couple of different ways. The easiest is probably to just go Preferences->Openbox->GUI Menu Editor (or press Alt-F2 and type 'obmenu').

To get rid of the panel, just edit your autostart.sh (also in the Preferences->Openbox menu) and add a # symbol at the beginning of the line to comment it out (and skip it during startup). If you're using the current version (9.04) the panel is named tint. I think there is also an option to turn the panel off in the Preferences menu (can't remember right now).

---

