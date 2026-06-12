---
title: "Logout / Shutdown dialog box"
date: 2009-01-17
forum: General Help
---

### Post by ugm6hr on 2009-01-17
On an essentially standard Hardy installation with Gnome, the logout dialog box takes a good 30-45 secs to appear,

Running "gnome-session-save --kill" in Terminal reveals nothing extra - Terminal simply stands with a cursor until the dialog box appears.

What could be doing this?

Details:
Everything else runs fine.
32-bit generic Ubuntu Hardy with Wicd instead of Network Manager, sshserver, wine, vino Remote Desktop.

---

### Post by DeMus on 2009-01-17
> **ugm6hr said:**
> On an essentially standard Hardy installation with Gnome, the logout dialog box takes a good 30-45 secs to appear,

Running "gnome-session-save --kill" in Terminal reveals nothing extra - Terminal simply stands with a cursor until the dialog box appears.

What could be doing this?

Details:
Everything else runs fine.
32-bit generic Ubuntu Hardy with Wicd instead of Network Manager, sshserver, wine, vino Remote Desktop.


Did you disable Powermanager?
System | Preferences | Sessions Preferences.
I did it once also and had to wait a very long time, now it's running again and I have no problems shutting down.

---

