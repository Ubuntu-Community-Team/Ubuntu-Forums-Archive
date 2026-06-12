---
title: "Ubuntu 12.10 not logging into correct session"
date: 2013-01-18
forum: Desktop Environments
---

### Post by floweringmind on 2013-01-18
I had my system working correctly but since the last updates I am having trouble with my session not working correctly.

If I log into Ubuntu default session and reboot it logs back into Ubuntu default session. But if I log into a Cinnamon session and reboot, it dumps me into a low video session of Gnome. If I log out and log back into Cinnamon everything is fine until I reboot.

I changed lightdm.conf to have: user-session=cinnamon
but that seems to have no effect.

I also purged Cinnamon and reinstalled it, but that doesn't fix it.

Help is much appreciated.

Chris

---

### Post by floweringmind on 2013-01-18
I was getting video tearing, so I ended up installing NVidia drivers manually from NVidia and that fixed the session issue as it rebuilt the xorg.conf file.

---

