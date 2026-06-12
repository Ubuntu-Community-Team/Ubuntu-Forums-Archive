---
title: "ubuntu psu check"
date: 2009-03-19
forum: General Help
---

### Post by 8James on 2009-03-19
I have a dell computer running ubuntu 8.10. How do I check the PSU load percentage without having to use the terminal? Thanks.

---

### Post by cariboo on 2009-03-19
I haven't tried this, I more worry about cpu  temps and fan speeds, but if you install lm-sensors and Hardware Sensor Monitor applet you can monitor psu voltages. Once you have installed lm-sensors open a terminal and run:

```
sudo sensors-detect
```

This will find what sensors are supported and loads the needed modules, once you have restarted right-click on which ever panel you want the hardware sensors applet to reside, add the Hardware Sensor Monitor, the once the applet is running, right-click and select preferences and setup what you want monitored.

See screenshot to see how I have set mine up.

Jim

---

