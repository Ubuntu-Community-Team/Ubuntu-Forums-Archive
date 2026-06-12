---
title: "One user cannot login via GDM"
date: 2010-12-11
forum: Desktop Environments
---

### Post by Orestez on 2010-12-11
Hi all,

Is it possible "reset" all (X, GDM related) permissions/settings of one user?

What would cause one specific user not to be able to log into **anything** via gdm/the login screen? After providing the proper password, the screen goes black and then jumps back to the login screen. No session alternative works, not even xterm or gnome failsafe. I can however log in via the console (Ctrl+Alt+F6, recovery etc). With another user I can log in via GDM just fine, and deleting and re-adding the "broken" user doesn't make any difference.

Some (maybe) relevent logs:
part of syslog:
> Dec 12 01:20:58 <specific user> pulseaudio[1358]: core-util.c: Home directory /etc/timidity not ours.
Dec 12 01:20:58 <specific user> pulseaudio[1358]: lock-autospawn.c: Cannot access autospawn lock.
Dec 12 01:20:58 <specific user> pulseaudio[1358]: main.c: Failed to acquire autospawn lock
Dec 12 01:20:59 <specific user> acpid: client connected from 1123[0:0]
Dec 12 01:20:59 <specific user> acpid: 1 client rule loaded
Dec 12 01:21:00 <specific user> gdm-session-worker[1397]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Dec 12 01:21:00 <specific user> rtkit-daemon[1406]: Sucessfully called chroot.
Dec 12 01:21:00 <specific user> rtkit-daemon[1406]: Sucessfully dropped privileges.
Dec 12 01:21:00 <specific user> rtkit-daemon[1406]: Sucessfully limited resources.
Dec 12 01:21:00 <specific user> rtkit-daemon[1406]: Running.
Dec 12 01:21:00 <specific user> rtkit-daemon[1406]: Watchdog thread running.
Dec 12 01:21:00 <specific user> rtkit-daemon[1406]: Canary thread running.
Dec 12 01:21:00 <specific user> polkitd[1410]: started daemon version 0.96 using authority implementation `local' version `0.96'
Dec 12 01:21:00 <specific user> rtkit-daemon[1406]: Sucessfully made thread 1404 of process 1404 (n/a) owned by '112' high priority at nice level -11.
Dec 12 01:21:00 <specific user> rtkit-daemon[1406]: Supervising 1 threads of 1 processes of 1 users.
Dec 12 01:21:01 <specific user> anacron[1445]: Anacron 2.3 started on 2010-12-12
Dec 12 01:21:01 <specific user> anacron[1445]: Normal exit (0 jobs run)
Dec 12 01:21:01 <specific user> rtkit-daemon[1406]: Sucessfully made thread 1449 of process 1404 (n/a) owned by '112' RT at priority 5.
Dec 12 01:21:01 <specific user> rtkit-daemon[1406]: Supervising 2 threads of 1 processes of 1 users.
Dec 12 01:21:01 <specific user> rtkit-daemon[1406]: Sucessfully made thread 1457 of process 1404 (n/a) owned by '112' RT at priority 5.
Dec 12 01:21:01 <specific user> rtkit-daemon[1406]: Supervising 3 threads of 1 processes of 1 users.
Dec 12 01:21:01 <specific user> gdm-simple-greeter[1393]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Dec 12 01:21:01 <specific user> acpid: client connected from 1502[107:114]
Dec 12 01:21:01 <specific user> acpid: 1 client rule loaded
Dec 12 01:21:01 <specific user> gdm-simple-greeter[1393]: WARNING: Unable to lookup user name cassandr: Success
Dec 12 01:21:14 <specific user> gdm-session-worker[1397]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Dec 12 01:21:16 <specific user> gdm-session-worker[1397]: pam_sm_authenticate: Called
Dec 12 01:21:16 <specific user> gdm-session-worker[1397]: pam_sm_authenticate: username = [<specific user>]
Dec 12 01:21:16 <specific user> gdm-session-worker[1506]: Passphrase file wrapped
Dec 12 01:21:18 <specific user> kernel: [   37.021309] padlock: VIA PadLock not detected.
Dec 12 01:21:22 <specific user> gdm-simple-slave[1594]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Dec 12 01:21:22 <specific user> acpid: client 1123[0:0] has disconnected
Dec 12 01:21:22 <specific user> acpid: client 1123[0:0] has disconnected
Dec 12 01:21:22 <specific user> acpid: client connected from 1596[0:0]
Dec 12 01:21:22 <specific user> acpid: 1 client rule loaded
Dec 12 01:21:23 <specific user> acpid: client connected from 1596[0:0]
Dec 12 01:21:23 <specific user> acpid: 1 client rule loaded
Dec 12 01:21:25 <specific user> gdm-session-worker[1633]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Dec 12 01:21:25 <specific user> gdm-simple-greeter[1630]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Dec 12 01:21:25 <specific user> gdm-simple-greeter[1630]: WARNING: Unable to lookup user name <specific user>: Success
Dec 12 01:21:27 <specific user> kernel: Kernel logging (proc) stopped.


Regards,
Orestez

---

### Post by slooksterpsv on 2010-12-11
Log in with an admin account and go to System -> Administration -> Users and Groups. Click on the user then click on Advanced Settings -> click on the Advanced tab and make sure they have like /bin/bash. If it has none or is empty, that may be the issue. I've ran into that a few times.

---

### Post by Orestez on 2010-12-12
Yeah, it says that... very weird. Must be an issue with a config file somewhere.

---

