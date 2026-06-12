---
title: "Selectable dual monitors?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by chadwick359 on 2006-07-11
I recently purchased a shiny new lcd monitor for a secondary monitor / desktop monitor, but not two weeks after buying it, my desktop died. I had some success setting up dual monitors with the display configuration utility in System Settings, but I'm looking for a way to be able to select using dual monitors at login, as I am not always at my desk. Is there a easy  way to add such an option to the Kdm sessions, or will it require some tricky scripting? If anybody could help me out with this, I'd be very greatful.

---

### Post by scxtt on 2006-07-11
i don't know about making it a session (tho i bet it's possible) - but you could have 2 xorg.conf files, one for dual and one for single ... a simple restart of X could load either one, you can probably even specify which version to use when starting X, instead of renaming one to xorg.conf all the time [using one called xorg_dual.conf & xorg_single.conf] ...

---

### Post by chadwick359 on 2006-07-11
That was pretty much the only way I could think to do it. I was going to make  /usr/bin/kdmd and kdms scripts that would copy the correct xorg.conf (dual or single) to /etc/X11/xorg.conf and execute kdm, but this seems sloppy and convoluted to me, so I was wondering if anybody knew of a better way to do it.

---

### Post by chadwick359 on 2006-07-12
Turns out that this is a lot easier than I originally thought it was going to be. X can be told to use a different config file just by adding the -config switch. As soon as I get home to get the script worked out I'll post it for anybody who wants it.

---

