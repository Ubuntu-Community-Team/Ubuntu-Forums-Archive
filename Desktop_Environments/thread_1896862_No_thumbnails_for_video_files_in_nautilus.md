---
title: "No thumbnails for video files in nautilus"
date: 2011-12-17
forum: Desktop Environments
---

### Post by avi9526 on 2011-12-17
Ubuntu 11.10
Gnome classic
No thumbnails for video files in nautilus. It's annoying.
In nautilus settings thumbnails is enabled.
gconf: "/desktop/gnome/thumbnailers" is empty.
How to solve?

---

### Post by Rytron on 2012-04-08
I've noticed that **some** videos don't have thumbnails in nautilus and thunar. There are no thumbnails at all in pcmanfm.

---

### Post by kiirokurisu on 2012-04-10
Try installing the package "ffmpegthumbnailer"

---

### Post by Rytron on 2012-04-11
> **kiirokurisu said:**
> Try installing the package "ffmpegthumbnailer"

No joy, thanks though. :confused:

---

### Post by kiirokurisu on 2012-04-11
Also, by default Nautilus won't create thumbnails for files larger than 10MB. Since most video files (ahem) are bigger than this, it's kind of a silly setting. To change it, open Nautilus and navigate to Edit -> Preferences -> Preview.

---

