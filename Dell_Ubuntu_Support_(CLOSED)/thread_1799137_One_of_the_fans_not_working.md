---
title: "One of the fans not working"
date: 2011-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bulva on 2011-07-07
While messing with my conky config I noticed that apparently one of the fans is not working.

The computer is dell alienware aurora desktop with:
Intel Core i7-2600K, 3.4GHz, 8MB Cache
NVIDIA GeForce GTX 590, 3GB GDDR5
SATA II, 1TB, 7.200rpm, 32MB Cache

And here's the sensors output that raised my eyebrow:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +36.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +37.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +37.0°C  (high = +80.0°C, crit = +98.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +35.0°C  (high = +80.0°C, crit = +98.0°C)

f71889a-isa-0290
Adapter: ISA adapter
in0:          +1.65 V  
in1:          +1.36 V  (max =  +2.04 V)
in2:          +1.14 V  
in3:          +0.86 V  
in4:          +0.69 V  
in5:          +1.36 V  
in6:          +1.66 V  
in7:          +1.65 V  
in8:          +1.66 V  
fan1:        1195 RPM
fan2:           0 RPM  ALARM
fan3:        3529 RPM
temp1:        +41.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +36.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp3:          FAULT  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

```I'm not sure which fan is what, the first temperature is probably GPU (more or less overlaps with what nvidia-settings report), the second is definitely the hard drive, I don't know what is the third that he fails to report (motherboard?).

---

