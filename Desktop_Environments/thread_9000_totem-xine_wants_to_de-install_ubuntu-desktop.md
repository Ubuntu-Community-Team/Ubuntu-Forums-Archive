---
title: "totem-xine wants to de-install ubuntu-desktop"
date: 2004-12-23
forum: Desktop Environments
---

### Post by nocturn on 2004-12-23
I tried to install totem-xine (suggested in the unofficial Ubuntu guide) on warty.

Synaptic says it will remove ubuntu-desktop if I want this package.

---

### Post by randy on 2004-12-23
I'm not sure if theres a question here but synaptic is correct.  Totem based on gstreamer is included in Ubuntu-desktop and totem and totem-xine can't be installed on the same system.  I did this and the only time it screwed me up was when I upgraded to hoary because I was missing a couple of packages.  It should be safe to do.

---

### Post by nocturn on 2004-12-23
[QUOTE=randy]I'm not sure if theres a question here but synaptic is correct.  Totem based on gstreamer is included in Ubuntu-desktop and totem and totem-xine can't be installed on the same system.  I did this and the only time it screwed me up was when I upgraded to hoary because I was missing a couple of packages.  It should be safe to do.[/QUOTE]

I'm very new to Ubuntu (2 days).  I was under the impression that removing Ubuntu-desktop would break the rest of my install.  This is not correct?

---

### Post by randy on 2004-12-23
No, it's just a metapackage.  Removing it won't break your system.

---

### Post by HughR on 2006-11-09
> **randy said:**
> No, it's just a metapackage.  Removing it won't break your system.Sorry for reviving such an old topic, but it still applies.

If you remove this metapackage, apparently upgrades between Ubuntu releases won't work properly.

All-in-all, this seems a bit dodgy.

---

