---
title: "Getting conky to show CPU/mobo temp"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by herbster on 2008-02-03
Sensors output:

```
~$ sensors
coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +38.0°C  (crit = +100.0°C)                  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +38.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +39.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +39.0°C  (crit = +100.0°C)                  

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.13 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +11.30 V  (min =  +8.18 V, max =  +1.74 V)   ALARM
AVCC:        +3.28 V  (min =  +0.69 V, max =  +0.43 V)   ALARM
3VCC:        +3.26 V  (min =  +0.40 V, max =  +0.29 V)   ALARM
in4:         +1.65 V  (min =  +1.82 V, max =  +0.30 V)   ALARM
in5:         +1.63 V  (min =  +0.00 V, max =  +0.91 V)   ALARM
in6:         +5.22 V  (min =  +0.95 V, max =  +4.92 V)   ALARM
VSB:         +3.28 V  (min =  +0.98 V, max =  +3.52 V)   
VBAT:        +3.23 V  (min =  +3.94 V, max =  +0.59 V)   ALARM
Case Fan:      0 RPM  (min =  421 RPM, div = 128)  ALARM
CPU Fan:    2033 RPM  (min = 37500 RPM, div = 4)  ALARM
Aux Fan:       0 RPM  (min =  958 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
Sys Temp:    +31.0°C  (high = +65.0°C, hyst = +50.0°C)  sensor = thermistor
CPU Temp:    +30.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:   +127.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
~$
```

Relevant part of conky that was working on old computer:

```
${execi 5 sensors | grep -A 0 'temp1' | cut -c15-16}${color #e8e8e8}C
${color #ffffff}${execi 5 sensors | grep -A 0 'temp2' | cut -c15-16}
```

Thanks for any help :)

EDIT: Solved, just had to change "temp1" and "temp2" in conky to "CPU Temp" and "Sys Temp" respectively.

---

