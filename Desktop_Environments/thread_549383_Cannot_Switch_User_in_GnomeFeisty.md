---
title: "Cannot Switch User in Gnome/Feisty"
date: 2007-09-12
forum: Desktop Environments
---

### Post by asterjolly on 2007-09-12
Hi!

When I simply try to Switch User through the shutdown/etc. icon, a box pops up with the message:

Cannot start new display
The X server failed.  Perhaps it is not configured well.

I click 'ok' and a second 'Error while running command' box pops up.  I click 'ok' to that and it just goes away, leaving me where I started.  The same happens when I try to switch user from a locked screen.  I'm afraid I don't know what to look for in configuring x in this case for it to work properly.  Any clues?

-aster

---

### Post by Happy_Man on 2007-09-12
Were you editing something in X config files before you noticed this happening?

---

### Post by asterjolly on 2007-09-27
Nope.. I have not touched any config files on my current install.  

Interestingly, now GDM will not work at all.  It hangs while loading and I have to ctrl-alt-f* then kill the process and startx to get into gnome at all.  Not sure if these two things are related but GDM is definitely having problems.  It is the newest version and I can't think of anything I changed before it stopped working.

---

### Post by DarrenCarlton on 2007-10-21
I'm having the same problem, and it started when I upgraded to the i195 driver for my Gateway MX6290 laptop (uses an intel driver for the monitor).

Given that it's been 3 weeks since anyone replied to this thread, I wonder if this is a known bug without a solution?

---

