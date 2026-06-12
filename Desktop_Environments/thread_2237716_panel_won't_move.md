---
title: "panel won't move"
date: 2014-08-03
forum: Desktop Environments
---

### Post by cmcanulty on 2014-08-03
all of the sudden my top panel doesn't go all the way to the top of screen so it hides my firefox menu see screenshot. I tried panel prefs so it gets a red outline but it is stuck and won't move up see screenshot

---

### Post by egeezer on 2014-08-03
Looks like you have panels at the top and the bottom.  You could try removing one of them to see how that works.  FWIW, I had some panel problems with Xfce on 14.04.1, which I solved by removing both panels and just replacing them fresh.  Worked fine for me, and the new ones did all the right things like move and resize.

---

### Post by cmcanulty on 2014-08-03
that is a last resort as I have a lot of tweaks! I got it from another search had to grab left edge of panel then moved it back to top edge, thanks

---

### Post by Dennis N on 2014-08-03
Just having the red outline isn't enough to allow it to be moved. Locking the panel prevents it from moving, so it's worth checking to see that this panel is not locked from: Panel Prefs > Display > General > (uncheck) Lock panel. That said, this seems unlikely, since to get the panel where it is it seems to me it would have to first be unlocked, moved, then locked again to prevent it from moving again.

---

