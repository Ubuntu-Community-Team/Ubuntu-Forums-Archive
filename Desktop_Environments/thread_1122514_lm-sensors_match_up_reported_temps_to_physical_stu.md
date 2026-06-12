---
title: "lm-sensors: match up reported temps to physical stuff"
date: 2009-04-11
forum: Desktop Environments
---

### Post by graysky on 2009-04-11
I've got lmsensors up and running on my DFI LP LT P35-T2R motherboard.  I think I can figure out what most of the data are but there are some that I don't really understand.

I am currently using Handbrake to encode some video files so the temps should be up:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +36.0°C  (crit = +64.0°C)                  

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.17 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.31 V  (min =  +1.28 V, max =  +1.68 V)   
in2:         +3.28 V  (min =  +2.78 V, max =  +3.78 V)   
in3:         +2.88 V  (min =  +2.67 V, max =  +3.26 V)   
in4:         +2.98 V  (min =  +2.50 V, max =  +3.49 V)   
in5:         +1.34 V  (min =  +0.58 V, max =  +1.34 V)   
in6:         +2.02 V  (min =  +1.04 V, max =  +1.36 V)   
in7:         +2.85 V  (min =  +2.67 V, max =  +3.26 V)   
in8:         +3.26 V
fan1:       1523 RPM  (min = 3245 RPM)
fan2:          0 RPM  (min = 3245 RPM)
fan3:          0 RPM  (min = 3245 RPM)
temp1:       +36.0°C  (low  = +127.0°C, high = +64.0°C)  sensor = thermal diode
temp2:       +39.0°C  (low  = +127.0°C, high = +64.0°C)  sensor = thermistor
temp3:       +43.0°C  (low  = +127.0°C, high = +64.0°C)  sensor = thermistor
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +45.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +50.0°C  (high = +76.0°C, crit = +100.0°C)
```
Obviously the coretemp-iso-000x data are the temps for cores0-3.   

My questions are what physical component of the system are the following measuring:

1) "Adapter: Virtual device temp1:       +36.0°C  (crit = +64.0°C)"
2) "temp1:       +36.0°C  (low  = +127.0°C, high = +64.0°C)  sensor = thermal diode"
3) "temp2:       +39.0°C  (low  = +127.0°C, high = +64.0°C)  sensor = thermistor"
4) "temp3:       +43.0°C  (low  = +127.0°C, high = +64.0°C)  sensor = thermistor"

One of those should be the northbridge temp, and one of those should be the CPU temp as it's reported in the BIOS (not temp of the cores).  What are the other two and how can I know for sure which is which?

---

