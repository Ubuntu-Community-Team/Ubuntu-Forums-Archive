---
title: "How do I reset gdm login theme..?"
date: 2007-04-24
forum: Desktop Environments
---

### Post by ponx on 2007-04-24
I changed the Gnome login theme to a third-party one but when the xserver restarts the gdm just hangs and i can't log back in.

I've tried reinstalling/restarting gdm but it has no effect, coz i guess it's still trying to load the broken theme.

Does anyone know how to reset the login theme back to the original from the command line..?

ponx

---

### Post by benjaminmorris on 2007-04-24
Hhmmm, I don't claim to be any kind of expert on the issue, but you might try logging in a CLI session and and looking in you ~/.gdm folder for any clues to reset it. Also, you could try manually editing the /etc/gdm/gdm.conf and gdm.conf-custom files to reset the login back to something like *human*. Other than that, you'll have to wait for a more experienced answer. :) 

Let us know when you get if fixed.

---

### Post by ponx on 2007-04-24
Cheers for that.  I commented out the new theme in gdm.conf-custom, but had to reboot - an x restart alone didn't work..!?

Anyway, fixed now...

ponx.

---

