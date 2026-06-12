---
title: "Installing a screensaver which calls a bash script"
date: 2012-02-29
forum: Desktop Environments
---

### Post by arbrctb on 2012-02-29
Hi,

Forgive me, I'm fairly new to thisand am wondering if someone could help me with an issue that is really holding me back. 

I'm currently using Ubuntu 10.04 LTS with Gnome and am trying to install a screensaver that will launch a bash script (gnome-session-save --force-logout), forcing a user logout.

I have created a .desktop file in /usr/share/applications/screensavers with the path to this bash script (/usr/lib/xscreensaver), however when I go to the Screensavers applet the new screensaver does not appear. I have tried specifying it manually in gconf but the screensaver does not work. The bash script is set to executable as well, and I have tried restarting.

I have also tried editing the desktop.en_GB.utf8.cache file /usr/share/applications but this does not have any effect either.

Could anyone shed some light on why this is not working?

Any help greatly appreciated.

---

