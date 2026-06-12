---
title: "I can only set 4:3 resolutions, my screen is 16:9. Using Ubuntu 10.04"
date: 2011-07-07
forum: Desktop Environments
---

### Post by MrSamuel on 2011-07-07
Under system > preferences > monitor I can select either 640 x 480 or 800 x 600 or 1024 x 768 which are all 4:3 aspect ratios, as my screen is 16:9 everything looks stretched. How can I set a 16:9 aspect ratio screen resolution?

---

### Post by searchfgold6789 on 2011-07-07
Have you installed all the drivers for your graphics card? They are easily installable and there is a menu item for it, Additional Drivers. If they are all installed, post back and I'll help you reconfigure xorg.

---

### Post by MrSamuel on 2011-07-08
I have run the 'additional drivers' program and it hasn't come up with anything...

---

### Post by searchfgold6789 on 2011-07-09
Try opening up a terminal and running,```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by MrSamuel on 2011-07-09
Thanks, but didn't work. Nothing happened/changed.

---

### Post by sguart on 2011-07-09
this means that ubuntu can't correctly detect your display, therefore obtaining the right refresh rate range. (most likely cuz your display is analog)

you need to find out the spec of your display and manually set your horizontal and vertical refresh rate in the xorg.conf

list your hardware spec so ppl can help you more.

---

