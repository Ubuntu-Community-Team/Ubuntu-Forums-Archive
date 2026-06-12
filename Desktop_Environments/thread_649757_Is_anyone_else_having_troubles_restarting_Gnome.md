---
title: "Is anyone else having troubles restarting Gnome?"
date: 2007-12-25
forum: Desktop Environments
---

### Post by schmolch on 2007-12-25
Hello,

im using Gutsy on 2 machines, a amd64 Desktop and a 32bit Thinkpad.

On both systems 99 out of 100 Gnome restarts fail.
After i leave gnome and log in again in gdm, the gnome desktop does not show up, only the wallpaper does, no panels, nothing else.
It does not matter if i quit gnome with the log-out function or by killing X with ctrl+alt+backspace.

I watched the .xession-errors file a few times and it had that gtk+ error in it that i have seen in many other various posts before:
```

(process:5812): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

```

Im wondering if i should file a bug report about that, what do you think?

---

