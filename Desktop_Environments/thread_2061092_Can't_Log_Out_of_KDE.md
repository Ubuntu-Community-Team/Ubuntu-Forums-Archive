---
title: "Can't Log Out of KDE"
date: 2012-09-21
forum: Desktop Environments
---

### Post by professorYaffle on 2012-09-21
I have a mixed ubuntu oneiric installation that is essentially kubuntu. I can give more details if it's relevant, but it does use kdm as the login manager. I normally use fluxbox as my desktop/window manager, but the kids use a full blown KDE setup, however I've just been told that my son can't log out - hasn't been able to for "a while."

I've verified that this is the case. Logged in as him, the logout, shutdown and restart buttons simply have no effect whatsoever that I can detect. Sleep and hibernate still work okay. The only way I can find to get out of the desktop is to kill the X server (Alt-SysRq-k) or 'sudo init 0' or similar.

Logged in as my daughter, all those buttons work fine. So I'm assuming that it must be an issue in his configuration and settings, but I've no idea where to start looking (there's nothing obvious arriving in .xsession-errors (if KDE uses that?) in response to clicking the logout button.)

If anybody could help even start to work out where to debug this it would be greatly appreciated.

---

### Post by ajgreeny on 2012-09-21
This may be a bit of a longshot, but does your son use the OpenOffice quickstart icon (or the same for LibreOffice) in the system tray?

In the past, using gnome, it used to cause exactly what you are saying is happening, ie, no shutdown, logoff, restart etc etc, or not using the GUI, at least.  It was still possible using terminal, but not from the GUI.  If you killed the OOo or LO quickstart icon everything returned to normal.

---

