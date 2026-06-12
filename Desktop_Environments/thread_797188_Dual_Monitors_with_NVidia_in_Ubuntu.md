---
title: "Dual Monitors with NVidia in Ubuntu"
date: 2008-05-17
forum: Desktop Environments
---

### Post by carfield on 2008-05-17
I've follow steps from [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html) but doesn't help at all...

---

### Post by NikoC on 2008-05-17
Do you use the restricted card drivers by Nvidia (available via Main Menu > System > Administration > Hardware drivers: enable the nvidia graphics driver and reboot when asked)? If so, just hit ALT + F2 and type:
nvidia-settings
In X Server Display Configuration you can setup your output
e.g. Detect Displays, set their resolution, set them as clones, etc.

---

### Post by carfield on 2008-05-17
> **NikoC said:**
> Do you use the restricted card drivers by Nvidia (available via Main Menu > System > Administration > Hardware drivers: enable the nvidia graphics driver and reboot when asked)? If so, just hit ALT + F2 and type:
nvidia-settings
In X Server Display Configuration you can setup your output
e.g. Detect Displays, set their resolution, set them as clones, etc.

I am not using the restricted card drivers by Nvidia , if I run Hardware drivers there is nothing for me to select... How can I install it? I already install the nvidia-new driver from package manager

---

### Post by NikoC on 2008-05-18
How about the solution offered in the following thread?
[http://ubuntuforums.org/showthread.php?t=797270&highlight=hardy+nvidia]("http://ubuntuforums.org/showthread.php?t=797270&highlight=hardy+nvidia")

---

### Post by carfield on 2008-05-18
Not really, but this one solve my problem , in fact my graph card is too new to support :-/

[http://adamspotton.com/node/1](http://adamspotton.com/node/1)

---

