---
title: "gamepad"
date: 2008-06-05
forum: Gaming &amp; Leisure
---

### Post by nonewmsgs on 2008-06-05
i have been playing around with joy2key.  it seems like it works ok for buttons but i can't find that dam .joy2key file to make any adjustments.  it detects my gamepad fine (with a symlink, of course).  but then i don't know how to "force" games to accept the analog stick.  i would rather have the 4 directions assigned as keys too.

i also tried joy2key-gtk (a frontend) but it says

```

Configure: error: Package requirements (gtk+-2.0 >= 2.6.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

i tried qjoypad (which looks very mint), but it says:

```

dependency is not satisfiable: libqt3c102-mt

```

and 99% of google has links for breazy badger and some weird bug it had.
i tried to update qt but apt said i have the latest version.

my gamepad is automatically detected by ubuntu and is properly calibrated.  there was a nice program for windows called controlhk that i miss...

---

### Post by Perfect Storm on 2008-06-05
First error: Install libgtk2.0-dev

Second: you might check earlier distro releases of ubuntu: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for it.

---

