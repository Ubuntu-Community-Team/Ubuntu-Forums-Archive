---
title: "twm suddenly unable to see keypresses in windows"
date: 2009-04-18
forum: Desktop Environments
---

### Post by Olin Shivers on 2009-04-18
I'm running a pretty standard version of Intrepid. I use twm for
a window manager, with the gnome environment (yes, I know, twm is
pretty old-school). I set various window commands on different
keys (mostly function keys). All of a sudden, these keypresses do
not work when the mouse is in a window or a title bar.

 To give a simple example, if you put the following in your
.twmrc, then whenever you press "x" while the mouse cursor
is in a window's title bar, twm should fire up an xterm for
you:
```

"x"  = : title  : ! "xterm &"

```
This no longer works, in titlebar, window or frame contexts.
It only works in the root context.

This behavior started for me yesterday.

I'm mystified. I have not been frobbing my .twmrc or other
X config files. I have rebooted the entire machine; the issue
persists. I conjecture some recent package I installed on an
apt-get dist-upgrade changed things somehow.

Any insights?

    -Olin

---

