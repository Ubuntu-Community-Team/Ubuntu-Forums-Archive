---
title: "SuperKaramba Widget Sensor problem"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by Brando569 on 2007-12-07
im using the [SysMaloon](http://www.kde-look.org/content/show.php/SysMaloon?content=61406) from KDE Look and it kind of works i have lm-sensors and hddtemp installed but they dont seem to be showing up in the widget, ive narrowed it down to a problem with the way it greps the values from lm-sensors.

for example, this is the code it uses:
```
sensor=program program="sensors | grep 'Core 1' | cut -d + -f 2 | cut -d ' ' -f 1" interval=10000 align=left color=255,255,0
```

but if i change it to 
```
 sensor=program program="sensors " interval=10000 align=left color=255,255,0
``` 

it displays the all of the values so im assuming its a problem with the way it grabs the values, although i dont know enough about this to mess with it on my own. :confused:

---

