---
title: "transparency in kiba-dock"
date: 2006-11-17
forum: Desktop Environments
---

### Post by eliabramo on 2006-11-17
my video adapter (SiS 650 on-board) doesn't support Aiglx\Beryl (or maybe I'm wrong?) but I was able to install kiba-dock from deb I found in Beryl forum, and it works fine, the icons jump all over the screen, but all the icons and the bar itself have a black background that was suppose to be transparent. I add the "composite" option to Xorg.conf and "xdpyinfo | grep Composite" returns "composite", so i believed that it works.
is my adapter doesn't support transparency, or there is something I could fix?

---

### Post by loell on 2006-11-17
> **eliabramo said:**
> my video adapter (SiS 650 on-board) doesn't support Aiglx\Beryl (or maybe I'm wrong?) but I was able to install kiba-dock from deb I found in Beryl forum, and it works fine, the icons jump all over the screen, but all the icons and the bar itself have a black background that was suppose to be transparent. I add the "composite" option to Xorg.conf and "xdpyinfo | grep Composite" returns "composite", so i believed that it works.
is my adapter doesn't support transparency, or there is something I could fix?

perhaps try innstalling xcompmgr
and the run it, and see if it does transparency

---

### Post by eliabramo on 2006-11-17
well, xcompmgr fix it! when i load it, i have transparency in the kiba-bar. should i load it on stratup?

---

### Post by loell on 2006-11-17
yes, atleast that is what my current settings, both xcompmgr and kiba-dock is set to startup.

---

