---
title: "Unable to notify my desktop"
date: 2010-12-14
forum: Desktop Environments
---

### Post by jeter on 2010-12-14
I'm trying to setup arpalert to send gnome notify messages to my desktop but its not working correctly. I think its because of the user but I'm not sThe script is executing correctly except i have a exec("/usr/bin/notify-send test") that triggers the gnome notify. If I run this under root, it works great. If I run this command (/usr/bin/notify-send test) under the arpalert user, it doesn't work.
ure.

In the configuration of arpalert, there is a setting called action on detect where you can execute a command

I'm doing this
action on detect = "/usr/share/arpalert/send_notify.php"

The script is executing correctly except I have a exec("/usr/bin/notify-send test") that triggers the gnome notify. If I run this php script or notify-send under root, it works great. If I run this command (/usr/bin/notify-send test) under the arpalert user, it doesn't work. I can execute php script but the exec inside doesn't seem to run and php_safe mode is off.

cat /etc/passwd | grep arpalert
arpalert:x:116:125:ARP Alerter,,,:/var/lib/arpalert:/bin/sh

Any suggestions?

---

