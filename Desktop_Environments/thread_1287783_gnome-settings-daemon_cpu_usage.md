---
title: "gnome-settings-daemon cpu usage"
date: 2009-10-10
forum: Desktop Environments
---

### Post by blakecraw on 2009-10-10
I use openbox, with my appearance properties set from my .gtkrc-2.0 file. I don't use gnome-settings-daemon, but occasionally I run something that invokes it (such as the keyboard preferences dialog, etc).

Whenever gnome-settings-daemon starts, it immediately goes to 20-100% cpu usage (as do some gnome applications that interact with it, such as gnome-panel, all the applets, etc). The only way to fix this is to kill gnome-settings-daemon, and all the affected applications, then they work fine when I restart them (as long as gsd isn't running).

I created a new user to test this, and with that user, whether I'm in GNOME or openbox, there is no problem with gnome-settings-daemon.

Does anybody know what I need to change with my configuration to fix this?

---

### Post by blakecraw on 2009-10-20
Still bugging me, any ideas?

---

### Post by mcduck on 2009-10-20
Try starting gnome-settings-daemon from a terminal and check if you see any error messages...

---

### Post by blakecraw on 2009-10-20
The only error message I get is:

```
(gnome-settings-daemon:11082): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:11082): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
```

which I also get when I run gnome-settings-daemon as a different user (which does not cause a problem).

The various programs that get bogged down by g-s-d don't give any error messages when I start it.

---

### Post by blakecraw on 2009-10-25
Still an issue, and one that I would like to get fixed before upgrading to 9.10 as I may need to use some of the gnome programs (keyboard/mouse preferences, etc) to smooth the upgrade process.

---

