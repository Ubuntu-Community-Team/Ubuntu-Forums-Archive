---
title: "Customize notification dialog?"
date: 2007-07-14
forum: Desktop Environments
---

### Post by fyllekajan on 2007-07-14
How do I change this notification dialog...

[IMG]http://www.ubuntu.com/files/u3/update-notification.png[/IMG]

...to look like this?

[IMG]http://www.manucornet.net/ubuntu/JPEG/Startup_notification_transp.png[/IMG]

I may be crazy but I really like the original GNOME notification dialogs. Don't have Ubuntu on the computer atm (going to reinstall it later) so haven't tried to change it myself yet, but if someone knows how to fix this please explain how. Thanks!

---

### Post by lucazade on 2007-07-14
Try this:

gconftool-2 -t string -s /apps/notification-daemon/theme Standard

---

### Post by fyllekajan on 2007-07-14
Thanks man! :)

---

