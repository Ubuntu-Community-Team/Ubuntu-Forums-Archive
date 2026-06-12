---
title: "Stange fluxbox/gnome behaviour"
date: 2007-04-20
forum: Desktop Environments
---

### Post by Swab on 2007-04-20
When I run nautilus from fluxbox, my desktop appears to change into some sort of bizarre gnome / fluxbox hybrid!  I have the fluxbox task bar but my gnome desktop including gnome menu when I right click.

Is this normal behaviour?

---

### Post by yabbadabbadont on 2007-04-20
That is not normal.  Nautilus is being launched with the wrong command line parameters.  It should have had  "--no-desktop" as a parameter when launched.  Check your ~/.fluxbox/menu file to see how it is being called.  Try running it from a terminal with that parameter and see if the behavior changes.

---

### Post by Swab on 2007-04-20
Thanks, issue resolved :)

---

