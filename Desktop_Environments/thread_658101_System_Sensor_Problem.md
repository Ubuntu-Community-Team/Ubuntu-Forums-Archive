---
title: "System Sensor Problem"
date: 2008-01-04
forum: Desktop Environments
---

### Post by mjmurf on 2008-01-04
Hi Folks,

I'm running Ubuntu 7.10 on an Asus P5N32SLI SE Deluxe mobo with an E6600 CPU.

I have installed  lm-sensors and I am getting sensor data, however, some of the values seem to be mislabeled.  for example CPU Temp and MoBo Temp are reversed.  The fans seem ok, but the voltages are all askew.  I have no idea where some of these voltage values are coming from.  There is nothing wrong with my power supply and checking these voltages in windows or the system bios everything checks out ok.  Here is a copy of my sensors output.  Any help would be appreciated.

```
it8712-isa-0d00
Adapter: ISA adapter
VCore 1:   +1.28 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:   +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:     +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+5V:       +6.85 V  (min =  +0.00 V, max =  +6.85 V)   ALARM
+12V:     +12.16 V  (min =  +0.00 V, max = +16.32 V)   
-12V:      +3.93 V  (min = -27.36 V, max =  +3.93 V)   ALARM
-5V:       +4.03 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:     +5.11 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +4.08 V
fan1:     2045 RPM  (min =    0 RPM, div = 4)          
fan2:     1371 RPM  (min =    0 RPM, div = 8)          
fan3:     1394 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +40°C  (low  =    -1°C, high =  +127°C)   sensor = diode   
CPU Temp:    +27°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
Temp3:      +128°C  (low  =    -1°C, high =  +127°C)   sensor = disabled   

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +41°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +45°C  (high =   +85°C)                   

```

---

