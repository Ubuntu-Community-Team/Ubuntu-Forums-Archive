---
title: "Win+L shortcut doesn't work, others work fine"
date: 2008-05-28
forum: Desktop Environments
---

### Post by Nesman on 2008-05-28
Specs:
Kubutnu 8.04 on Dell Latitude D820
Running KDE 3.5.9
Happens with or without desktop effects.

I have configured the shortcut Win+L to lock my session, but it is ignored.  Other Win+* shortcuts work, such as Win+Tab to rotate the cube.

Lock Session works if assigned to another shortcut, such as ctrl+alt+L, and works from the menu.

Edit:
Fixed.
I figured the shortcut was assigned elsewhere, but couldn't find it in the Keyboard and Mouse settings.  I found it in the CompizConfig Settings Manager > Enhanced Zoom Desktop > Zoom Area Movement > Toggle Zoom Area Lock.

I only found it because I was experimenting with assigning the shortcut to a different action and CCSM alerted me of the conflict.  After disabling this shortcut I am able to use it in the standard settings again.

It seems like I had to play with it a bit before it took, but within 3 minutes of disabling it from Compiz I was working.

---

