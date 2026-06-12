---
title: "lm-sensors temp report AMD"
date: 2011-07-29
forum: Desktop Environments
---

### Post by Drak3 on 2011-07-29
hey, i was wondering if any one knew if the separate bit at the bottom of this:

```
john@unimatrix434:~$ sensors
it8720-isa-0228
Adapter: ISA adapter
in0:         +1.36 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.50 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +3.06 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.16 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.10 V
fan1:       1007 RPM  (min =   10 RPM)
fan2:        938 RPM  (min =   10 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan5:       1333 RPM  (min =   10 RPM)
temp1:       +41.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +43.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
temp3:       +51.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +0.513 V

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +39.0°C
```

is actually the cpu temp as reported my the CPU?  that was the goal, obviously, but its showing one temp, not 6....

btw, i know in reality, if this is the cpu temp, its 15C hotter than reported.  just running mprime and want to make sure i dont get too hot.

---

