---
title: "fans reading 0 rpm in sensors-applet"
date: 2008-09-03
forum: Desktop Environments
---

### Post by dreaminhere on 2008-09-03
Using 64 bit 8.04 with a abit ip-35 mobo and intel quad core.  I can see all my temps but no rpm on my fans.  I have a cpu fan and two case fans

If I run sensors I get 

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.21 V  (min =  +0.00 V, max =  +1.74 V)
in1:         +7.29 V  (min =  +6.76 V, max =  +3.48 V)   ALARM
AVCC:        +3.18 V  (min =  +2.59 V, max =  +0.80 V)   ALARM
3VCC:        +3.18 V  (min =  +0.74 V, max =  +2.06 V)   ALARM
in4:         +1.26 V  (min =  +1.03 V, max =  +1.03 V)   ALARM
in5:         +1.10 V  (min =  +2.04 V, max =  +1.68 V)   ALARM
in6:         +3.51 V  (min =  +2.46 V, max =  +3.30 V)   ALARM
VSB:         +3.18 V  (min =  +0.02 V, max =  +0.61 V)   ALARM
VBAT:        +3.15 V  (min =  +0.00 V, max =  +1.06 V)   ALARM
Case Fan:      0 RPM  (min =    0 RPM, div = 128)
CPU Fan:       0 RPM  (min = 5273 RPM, div = 128)  ALARM
Aux Fan:       0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan4:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
Sys Temp:    +35.0°C  (high = -64.0°C, hyst = -127.0°C)  ALARM  sensor = thermistor
CPU Temp:    +17.0°C  (high = +80.0°C, hyst = -127.0°C)  sensor = diode
AUX Temp:    -11.5°C  (high = -126.5°C, hyst = +75.5°C)  sensor = thermistor


Any ideas how to get the fans to show proper rpm?

---

### Post by dreaminhere on 2008-09-06
bump

---

### Post by RedSquirrel on 2008-09-06
Have a look [here]("http://www.lm-sensors.org/wiki/FAQ/Chapter3#Fanssometimesalwaysread0").

---

