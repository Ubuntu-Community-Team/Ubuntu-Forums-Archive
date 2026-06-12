---
title: "GNOME missing almost everything after remote hang"
date: 2006-05-23
forum: Desktop Environments
---

### Post by Slim Odds on 2006-05-23
Hi All,

The other day, I was using GNOME remotely via X on my home LAN. The graphic interace hung. I killed my X server (on a Windows machine with cygwin).

Now, when I log into GNOME (local or remote, it doesn't matter) I get a terminal window and gkrellm. No window manager, no panel, no task bar, no icons, nothing else. :cry:

How do I fix this?

Everyone else on this machine is fine, it's just me.

I can also log in using KDE, or IceWM, or Elightenment. But I want my GNOME back.

P.S. I'm a long time linux geek and this one still shakes my confidence in the "robustness" of linux.

---

### Post by tuxcantfly on 2006-05-23
alt- f2 gnome-panel
alt-f2 nautilus
alt-f2 metacity

see if these fix anything. If they do, run

gnome-session-properties

and add these commands to startup

---

### Post by Slim Odds on 2006-05-23
[QUOTE=tuxcantfly]alt- f2 gnome-panel
alt-f2 nautilus
alt-f2 metacity

see if these fix anything. If they do, run

gnome-session-properties

and add these commands to startup[/QUOTE]

Thanks, but there is nothing to handle Alt-F2

There is NO WINDOWS MANAGER, NO PANEL, NO TASK BAR

Just terminal windows (that won't take input BTW) and gkrellm.

If it's any help at all, the splash screen shows, there is the start-up sound but none of the icons show in the slash window (which would normally be the panel, task bar, window manager, etc).

This is really insane.

---

### Post by tuxcantfly on 2006-06-22
reinstall gnome-session; it might fix some stuff. also, delete your .gconf directory to reset all settings, you might have messed them up

---

