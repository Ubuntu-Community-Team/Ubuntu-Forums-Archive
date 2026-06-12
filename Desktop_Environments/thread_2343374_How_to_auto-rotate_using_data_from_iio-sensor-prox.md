---
title: "How to auto-rotate using data from iio-sensor-proxy?"
date: 2016-11-15
forum: Desktop Environments
---

### Post by annevanrossum on 2016-11-15
I'm running iio-sensor-proxy from [https://github.com/hadess/iio-sensor-proxy](https://github.com/hadess/iio-sensor-proxy) which generates proper d-bus messages.

&#10140;  ~ monitor-sensor
    Waiting for iio-sensor-proxy to appear
+++ iio-sensor-proxy appeared
=== Has accelerometer (orientation: undefined)
=== Has ambient light sensor (value: 0.000000, unit: lux)
    Accelerometer orientation changed: normal
    Light changed: 1.000000 (lux)
    Accelerometer orientation changed: left-up
    Accelerometer orientation changed: normal
    Accelerometer orientation changed: right-up
    Accelerometer orientation changed: normal
    Accelerometer orientation changed: bottom-up
    Accelerometer orientation changed: left-up
    Accelerometer orientation changed: normal

With gnome this is picked up by gnome-settings-daemon if I'm correct. How do I inform lightdm to use this information to auto-rotate the screen? Although it's definitely possible to run my own script to pull all the time for changes, I prefer to have it in an event loop that checks d-bus anyway, so I'm not suddenly creating some kind of battery drain.

---

