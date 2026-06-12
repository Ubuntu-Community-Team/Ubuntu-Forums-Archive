---
title: "Failure to sleep and xsession crashing"
date: 2012-08-29
forum: Desktop Environments
---

### Post by afoglia on 2012-08-29
After running for a few days, my KDE/Kubuntu session is crashing when I try to sleep.  I shut my screen, and (a) the laptop won't go to sleep, (b) when I open my lid, I get the login screen, and switching to the text-only terminals (Ctrl-Alt-F2) just gives me a blank screen.

I've attached the syslog of the most recent failure, at Aug 29 01:42.  There was a successful sleep at Aug 28 09:33 in the same log.  The logs appear the same, until these pulseaudio errors.

```
Aug 29 01:42:23 envy kernel: [169553.070258] PM: Preparing system for mem sleep
Aug 29 01:43:09 envy pulseaudio[4040]: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
Aug 29 01:43:11 envy pulseaudio[4046]: [pulseaudio] pid.c: Stale PID file, overwriting.
Aug 29 01:43:11 envy pulseaudio[4046]: [pulseaudio] bluetooth-util.c: Error from ListAdapters reply: org.freedesktop.DBus.Error.AccessDenied
Aug 29 01:43:12 envy pulseaudio[4046]: [pulseaudio] server-lookup.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-lAgU82KnFE: Connection refused
Aug 29 01:43:12 envy pulseaudio[4046]: [pulseaudio] main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-lAgU82KnFE: Connection refused

```

I see nothing odd in the pm-suspend.log.

Unfortunately, I have no Xorg log from then.  After this message, at 1:43, a new Xorg.0.log file is started, and the old one must have been deleted.

In case it's actually a hardware problem, my laptop is an HP Envy 14 (2010 edition).

---

