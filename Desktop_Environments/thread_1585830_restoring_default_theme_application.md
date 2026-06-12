---
title: "restoring default theme application"
date: 2010-10-01
forum: Desktop Environments
---

### Post by AdX9170 on 2010-10-01
hey m a complete noob in ubuntu.. i ended up installing emerald theme manager n set it as default. how do i restore my default theme manager??

---

### Post by sikander3786 on 2010-10-01
If you just want to revert back, you can uninstall emerald.

If you want to keep emerald, for a newb, the best way is to install fusion-icon.

```

sudo apt-get install fusion-icon

```

It will appear under Applications > System Tools. It sits in the system tray and lets you select your theme manager/window manager and reloads them if needed.

You can configure it for auto start on boot by going to System > Preferences > Startup Application. Add new and enter "fusion-icon" in the command without quotes.

---

