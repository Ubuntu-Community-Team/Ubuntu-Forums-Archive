---
title: "Sensors-applets does not measure FANs but sensors do"
date: 2009-03-14
forum: Desktop Environments
---

### Post by lzap on 2009-03-14
Hi,

my sensors-applets does not measure FAN speed, temps are ok.

The command "sensors" is configured and works ok in the console (shows everything). Whats wrong? I thougt sensors-applets uses lm-sensors for data...

```
$ sensors
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.15 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.87 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.26 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.91 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.03 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +1.23 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +3.10 V  (min =  +0.00 V, max =  +4.08 V)   
in8:         +3.30 V
fan1:          0 RPM  (min =    0 RPM)
fan2:        875 RPM  (min =    0 RPM)
fan3:        473 RPM  (min =    0 RPM)
temp1:       +33.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +23.0°C  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
temp3:        -1.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +0.000 V

```

---

### Post by lzap on 2009-03-14
I have had to remove the applet and insert it again on the panel.

This broke up after upgrade. Its ok now.

---

