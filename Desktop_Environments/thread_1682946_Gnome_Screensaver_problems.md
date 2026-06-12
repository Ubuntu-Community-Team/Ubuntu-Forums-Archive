---
title: "Gnome Screensaver problems"
date: 2011-02-06
forum: Desktop Environments
---

### Post by Charlie69v on 2011-02-06
I installed xscreensaver thinking it would be cool, and now i hate it. so I removed packages via synaptic and it hasnt done anything. i want to know how to re-enable gnome screensaver as the default
much appreciated

---

### Post by towheedm on 2011-02-06
> **Charlie69v said:**
> I removed packages via synaptic and it hasnt done anything

Does this mean that xscreensaver still runs or just that the gnome screensaver does not run after removing xscreensaver?

To re-enable the gnome screensaver, click on System > Preferences > Startup Applications and check if there's a screensaver entry in the programs.

If so, click on edit and check the command, it should be 'gnome-screensaver'.  If it's xscreensaver, change it and that should be it.

If there isn't a screensaver entry, then click Add to add it.  Make sure the command is 'gnome-screensaver'.

---

### Post by Charlie69v on 2011-02-06
> **towheedm said:**
> Does this mean that xscreensaver still runs or just that the gnome screensaver does not run after removing xscreensaver?

To re-enable the gnome screensaver, click on System > Preferences > Startup Applications and check if there's a screensaver entry in the programs.

If so, click on edit and check the command, it should be 'gnome-screensaver'.  If it's xscreensaver, change it and that should be it.

If there isn't a screensaver entry, then click Add to add it.  Make sure the command is 'gnome-screensaver'.
I edited it and it worked perfectly, thanks!

---

