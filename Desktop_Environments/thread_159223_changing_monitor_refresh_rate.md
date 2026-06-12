---
title: "changing monitor refresh rate?"
date: 2006-04-12
forum: Desktop Environments
---

### Post by binilbenjamin on 2006-04-12
is there any way to change the monitor refresh rate??my current rate is 60Hz..and i'm not able to change it in the preference menu,as the only menu in the refresh rate menu is 60...is there any config file for tht purpose??

---

### Post by Ramses de Norre on 2006-04-12
sudo gedit /etc/X11/xorg.conf
Search for the monitor section (example below) and add the last 2 lines from the example with your correct values.
```
Section "Monitor"
    Identifier    "Packard Bell"
    Option        "DPMS"
    HorizSync    30-60
    VertRefresh    48-70
```

---

### Post by 5-HT on 2006-04-12
Safest way would be to edit the HorizSync and VertRefresh values in the monitor section of xorg.conf (/etc/X11/xorg.conf).

You can find these values either in the monitor's documentation, or perhaps a quick google search.

It is important to make sure you input the correct values, as you could do physical damage to the monitor if they are incorrect.

After they are set correctly, and the resolutions are what you want (and supported), you should be able to select the supported refresh rates.

HTH


*Too late.

---

