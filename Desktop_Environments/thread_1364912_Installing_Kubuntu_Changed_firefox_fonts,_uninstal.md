---
title: "Installing Kubuntu Changed firefox fonts, uninstalling kubuntu didn't fix them back.."
date: 2009-12-26
forum: Desktop Environments
---

### Post by sexyclient2 on 2009-12-26
I thought the kubuntu beta would be stable so I installed it, but it I couldn't even login to the desktop.  Long-story-short, I 1) installed kubuntu netbook & desktop from beta, 2) and went to system settingss in the fonts section & forced the dpi to 96, 3) reopened the system settings & disabled forced dpi, 4) and finally uninstalld kubuntu (using "completely remove," from synaptic,) but the damned fonts in firefox still look different. 

(I think subpixel hinting is off? But still, though) now I can't get the firefox fonts the way they were on default ubuntu install.

Any way to get them back?

---

### Post by sexyclient2 on 2009-12-26
I hate these fonts :(

---

### Post by Zorael on 2009-12-26
Remove or rename your **~/.fonts.conf** file.

---

### Post by sexyclient2 on 2009-12-26
> **Zorael said:**
> Remove or rename your **~/.fonts.conf** file.
JACKPOT~!  That worked like a charm, thanks!

---

