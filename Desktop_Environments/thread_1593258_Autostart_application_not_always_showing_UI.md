---
title: "Autostart application not always showing UI"
date: 2010-10-11
forum: Desktop Environments
---

### Post by double1116 on 2010-10-11
I have an intermittent problem with an autostart application in GNOME. This is Ubuntu 10.04 with the latest updates. I have a .desktop file in /etc/xdg/autostart that launches Unison to sync files on login. Unison has a gtk UI that should show up. On my fast computer (P4 3.4Ghz) it always shows. On my slow computer (P3 844Mhz) sometimes the UI does not show up. In the process list I see it running, but no UI. When this happens the nautilus process that shows the desktop also does not show the desktop, but nautilus is running. If after GNOME is up I kill the processes and manually restart they work fine.

It seems there is some timing issue here with GNOME not being initialized to the point that it will show the apps. I can add sleep to the Unison process, but I'd rather not because I'd be guessing on the timeout. It won't help nautilus though.

Ideas?

---

