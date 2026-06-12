---
title: "Refresh rate"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by ABX on 2007-08-10
Hi!

This is my first Linux installation and so far it looks awesome. But I have an issue. :(

The refresh rate is a PITA.

I have read some posts here and the best I could achieve is 85Hz.

I have a 19' CRT monitor and I watch it at 1024x768@120Hz. I tried various Xorg settings and nvidia-setting, but I can't get above 85Hz.

Any help would be welcome.

-------------------------------
Great success!

Added the monitor string calculated here: [http://sh.nu/nvidia/gtf.php](http://sh.nu/nvidia/gtf.php)
to xorg.conf, selected 53Hz (or a stupid number like this) and now i have 120Hz refresh rate!

---

