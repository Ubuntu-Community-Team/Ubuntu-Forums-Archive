---
title: "jaunty 9.04 New Notification System - NOT HERE"
date: 2009-04-24
forum: General Help
---

### Post by wynneth on 2009-04-24
I upgraded to the Jaunty RC and then did all the fresh updates today. I'm still seeing the same old balloon notifications as I've seen since 8.04. Is there something I need to verify here, because I'm under the impression I should be seeing the new notifications.

---

### Post by wynneth on 2009-04-24
I solved this myself. For some reason when I upgraded notify-osd was not installed, so the system was still using the old notification-daemon. I should point out that this would seem to say if you hate the new style just remove the notify-osd package and make sure you have notification-daemon.

---

