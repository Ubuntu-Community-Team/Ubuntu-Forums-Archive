---
title: "lm-sensors - no sensors were detected"
date: 2009-02-06
forum: General Help
---

### Post by vangs.a on 2009-02-06
kernel is 2.6.27-11
I have upgraded my mobo (P45 + ICH10 chipset), sensors used to work with the previous one. 
When I run sensors-detect I Get the following

sensors-detect revision 5249
.............
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH10

.....................
Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

Would appreciate your help

---

### Post by LowSky on 2009-02-06
did you check out those websites the tell you to check out

---

### Post by vangs.a on 2009-02-07
Yes. ICH10 is in the supported.

---

