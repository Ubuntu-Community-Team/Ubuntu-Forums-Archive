---
title: "minimise all windows / show desktop"
date: 2012-07-14
forum: Desktop Environments
---

### Post by jasonjob on 2012-07-14
Okay, yes, it's been addressed many times before, but I've never seen my particular problem come up.

Using a clean install of Ubuntu 12.04, with Gnome Classic for the desktop.

I have set super-d to minimise all windows / show the desktop.  But when I use it, something odd happens.  Instead of minimising to the task bar, my windows vanish momentarily and then slide back into place from the corners of the screen.  Do it again and they slide on from the diagonally opposite corner.

Anyone else ever had this happen?

---

### Post by billcauley on 2012-07-14
I used the "Show Desktop" applet from the "add to panel"; I get nothing with super-d. Also, I use five desktops, one of which is always clear. Switching to an unused desktop has the same effect, and so I never use the applet.

---

### Post by jasonjob on 2012-07-14
Worked it out.  Compiz came configured with  the show desktop module turned on.  It interferes with Gnome's basic show desktop function.  Disabled that module and all works as it should.  Wierd, and silly.

---

