---
title: "lxpanel configs"
date: 2009-04-17
forum: Desktop Environments
---

### Post by Thingymebob on 2009-04-17
I have LXDE Ubuntu 9.04 on an old PIII 500 256Mb running real nice. I also have a 6 year old who is in the habit of clicking things without knowing what they do.

He recently deleted his panels so couldn't start anything or logout. In an attempt to prevent him from doing the same again I changed the file permissions of the configs in his ~/.config/lxpanel/LXDE/panels/ to rw-r-r, group and owner to root. However its still possible to right click a panel, choose "delete this panel" and the config disappears, how?

If I ps aux | grep lxpanel, then its confirmed as running as his user which does not exist in any admin groups or /etc/sudoers

---

