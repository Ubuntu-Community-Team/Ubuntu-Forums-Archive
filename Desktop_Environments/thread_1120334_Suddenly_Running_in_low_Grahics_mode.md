---
title: "Suddenly Running in low Grahics mode"
date: 2009-04-08
forum: Desktop Environments
---

### Post by deamon_knight on 2009-04-08
I have Xubuntu on an old machine that is booting, but now reports "ubuntu is running in low graphics mode" Looks like X isn't starting properly. Letting ubuntu start in low graphics mode dumped me to tty1, and it looked like X restarted and then asked to detect my display. Choosing defaults did the same thing, and then I got to the desktop and it looked normal. Same problem after reboot. I tried installing updates and ended up with the same error, but now I'm stuck at 640x480 resolution. Any advice?

---

### Post by jobix on 2009-04-08
No solution here, but I ran into the same problem. Had an old machine lying around. Installed Xubuntu. Worked fine for a few days before it did the switcheroo. Now's it's in the low graphics mode. I tried to do a dpkg-reconfigure and even manual edits of the xorg.conf file but nothing helped. I might just reinstall the whole thing.

---

### Post by killerdogg77 on 2009-04-09
Had similar problem last weekend had to reinstall my video driver to get mine to load

---

### Post by Mochabuntoo on 2009-04-09
I have the exact same issue with Ubuntu 8.10, booted it up one morning and *bam*, 640x480 glory.

Poked around looking for a fix, even did a complete reinstall to no avail.

xorg.0.log seems to indicate that my nVidia drivers don't seem to want to talk to my monitor anymore... :(

'Unable to get display device DFP-0's EDID; cannot compute DPI from DFP-0's EDID.'

Any thoughts on how I might force a higher resolution?

---

### Post by deamon_knight on 2009-04-09
a Ctrl-ALt-BkSpc worked for me, even though changing the resolution with desktop properties scrambles it. It looks like it just keeps start/killing X until it works, then works until a resolution change and the process starts again. This is on an ATI card for me. It looks like I'm using the opensource driver, how could I reinstall that?

---

