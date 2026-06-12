---
title: "Gnome screensaver issue - after unlock screen goes blank / black"
date: 2007-03-19
forum: Desktop Environments
---

### Post by kg00005 on 2007-03-19
Hi All,

I have a gnome screensaver issue in Ubuntu 6.10 (kernel 2.6.17-50).

After locking/unlocking screensaver, my screen goes blank / black and I must killall gnome-screensaver, and start it again.
Very annoying..

gnome-screensaver-preferences freezes every time I start it, showing this:

[B]libGL warning: 3D driver claims to not support visual 0x4b
gnome-screensaver-Message: Found best visual for GL: 0x25
[/B]
I have to close the window manually

I have reinstalled (apt get remove --purge and install) it, but no changes. I also removed ~//.gconf/apps/gnome-screensaver dir!

Any ideas?

Thanks,
G

---

### Post by kg00005 on 2007-03-19
Hi,

Finally I solved the problem myself.
Probably one of the xscreensaver packages was missing, and that caused gnome-screensaver working badly.

**sudo apt -get install xscreensaver xscreensaver-data xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra**

Regards,
G

---

