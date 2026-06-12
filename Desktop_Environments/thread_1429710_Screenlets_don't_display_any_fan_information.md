---
title: "Screenlets don't display any fan information"
date: 2010-03-14
forum: Desktop Environments
---

### Post by El_Matthews on 2010-03-14
In the past I had my screenlets configured to show the speed of all my fans in my PC.

Now for some strange reason this isn't possible anymore. When I configure a the SensorsScreenlet (screenlet supposed to display info from lm-sensors) I only get the following possibilities:
CPU0, CPU1 , CPU2, RAM , SWAP, /

Where are all the other possibilities gone or why don't I see them anymore?

When I check lm-sensors with the command sensors I still got the info available:

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.12 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.51 V  (min =  +0.00 V, max =  +2.53 V)   ALARM
AVCC:        +3.28 V  (min =  +1.25 V, max =  +2.05 V)   ALARM
3VCC:        +3.28 V  (min =  +3.65 V, max =  +0.51 V)   ALARM
in4:         +1.41 V  (min =  +1.02 V, max =  +0.00 V)   ALARM
in5:         +1.68 V  (min =  +0.13 V, max =  +0.00 V)   ALARM
in6:         +4.53 V  (min =  +0.97 V, max =  +0.59 V)   ALARM
VSB:         +3.28 V  (min =  +0.00 V, max =  +1.02 V)   ALARM
VBAT:        +2.08 V  (min =  +2.05 V, max =  +0.83 V)   ALARM
Case Fan:   1854 RPM  (min = 2596 RPM, div = 8)  ALARM
CPU Fan:    1424 RPM  (min = 337500 RPM, div = 4)  ALARM
Aux Fan:    2327 RPM  (min = 6490 RPM, div = 4)  ALARM
fan5:       2343 RPM  (min = 2163 RPM, div = 8)
Sys Temp:    +27.0°C  (high = +64.0°C, hyst = +83.0°C)  sensor = thermistor
CPU Temp:    +27.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +124.5°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +1.950 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +32.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +32.0°C  (high = +78.0°C, crit = +100.0°C)  


Anybody an idea or a tip?

---

