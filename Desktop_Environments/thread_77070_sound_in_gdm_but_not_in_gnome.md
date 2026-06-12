---
title: "sound in gdm but not in gnome"
date: 2005-10-16
forum: Desktop Environments
---

### Post by psiko on 2005-10-16
gdm sounds at start, but gnome don't sound. I tried to start volume control but it says that the volume control devices were not found.

---

### Post by Lord Illidan on 2005-10-16
Try writing ```
killall esd
``` in a terminal.

---

