---
title: "notify-osd stuck in debug mode...arggh...frustrated"
date: 2010-12-18
forum: Desktop Environments
---

### Post by RiskySeven on 2010-12-18
Hi.  I believe my notify-osd package is stuck in debug mode.  Any idea what could be causing this?  Been this way for a loooong time....just now getting around to fixing it :)

This explain my issue perfectly....all notification bubbles appear this way...
[http://wwww.ubuntuforums.org/showthread.php?t=1362296](http://wwww.ubuntuforums.org/showthread.php?t=1362296)

A little history on notify-osd debug mode:
[http://ubuntuforums.org/showthread.php?t=1193705](http://ubuntuforums.org/showthread.php?t=1193705)

Things I've already tried to fix it:
rm -rf .gconf .gconfd .gnome2 .gnome2_private....reboot

contents of my /usr/share/dbus-1/services/org.freedesktop.Notifications.service (notice no 'DEBUG=1'):
[D-BUS Service]
Name=org.freedesktop.Notifications
Exec=/bin/sh -c 'if [ ! -x /usr/lib/notification-daemon/notification-daemon ] || [ "${GDMSESSION%.desktop}" = gnome ] || [ "${GDMSESSION%.desktop}" = guest-restricted ] || [ "${GDMSESSION%.desktop}" = default -a "$(basename `readlink /etc/alternatives/x-session-manager`)" = gnome-session ] || [ "${GDMSESSION%.desktop}" = une ]; then exec /usr/lib/notify-osd/notify-osd; else exec /usr/lib/notification-daemon/notification-daemon; fi'


If you can figure this out I'll buy you a virtual beer! :)

---

### Post by Krytarik on 2010-12-18
What about re-installing the notify-osd package?

By that way, I suggest trying the patched version to make it modify-able:
[http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

---

