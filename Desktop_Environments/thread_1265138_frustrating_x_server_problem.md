---
title: "frustrating x server problem"
date: 2009-09-13
forum: Desktop Environments
---

### Post by blackmail on 2009-09-13
My problem is that whenever I cange the resolution of the screen, after a reboot it turns back to default. I have an nVIDIA card, 5200, and I used Envy to install the drivers. If i start the Display settings manager it prompts me to use the nVidia control panel, and whenever i change the resolution of the screen, and save the settings, the programe replies that in can't parse the xorg.conf file. Could someone suggest something.

---

### Post by 3rdalbum on 2009-09-13
Sometimes you need to add the resolution to xorg.conf manually.

---

### Post by blackmail on 2009-09-21
Well i have actually found that if I set the resolution whitout the nVIDIA thing the resolution actually remains the same after a reboot. This seems to have solved my problem! I would prefer not to edit the xorg.conf file manually, because i have done that in the past and have utterly blown away my PC.

---

### Post by theZoid on 2009-09-21
> **blackmail said:**
> Well i have actually found that if I set the resolution whitout the nVIDIA thing the resolution actually remains the same after a reboot. This seems to have solved my problem! I would prefer not to edit the xorg.conf file manually, because i have done that in the past and have utterly blown away my PC.

```
sudo nvidia-settings
```

then save to xorg

---

### Post by blackmail on 2009-09-22
thank you, nice idea...
Neved tought of this one :P

---

