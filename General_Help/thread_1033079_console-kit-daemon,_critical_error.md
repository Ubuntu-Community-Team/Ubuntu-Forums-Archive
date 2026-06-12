---
title: "console-kit-daemon, critical error"
date: 2009-01-07
forum: General Help
---

### Post by cdnjay on 2009-01-07
Hello folks,

Just wondering if anyone has any thoughts on the problem below (pulled from the syslog of a Ubuntu Server 8.10 system.)  Doesn't seem to be causing me any problems currently but at the same time I'd like to clear my server log of as many "Critical" errors as possible before it has to play ball on Friday. :)

```
console-kit-daemon[4824]: WARNING: Unable to activate console: No such device or address
Jan  6 20:44:41 M155 console-kit-daemon[4824]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Jan  6 20:44:41 M155 console-kit-daemon[4824]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' fail
ed
```

Thanks!

Jason

---

### Post by bambam82 on 2009-01-21
Hi, I have the same things in my log.

```
Jan 21 12:45:28 bama console-kit-daemon[4416]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Jan 21 12:45:28 bama console-kit-daemon[4416]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Jan 21 12:45:31 bama init: tty1 main process ended, respawning
Jan 21 12:45:31 bama console-kit-daemon[4416]: WARNING: Unable to activate console: No such device or address
Jan 21 12:45:31 bama console-kit-daemon[4416]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)'
Jan 21 12:45:31 bama console-kit-daemon[4416]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Jan 21 12:45:31 bama console-kit-daemon[4416]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

---

