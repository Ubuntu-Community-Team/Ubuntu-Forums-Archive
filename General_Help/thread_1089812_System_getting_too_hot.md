---
title: "System getting too hot?"
date: 2009-03-07
forum: General Help
---

### Post by Tulitikku on 2009-03-07
I finally got LM-Sensors installed today, i ran a quick check and this is what i got:
               
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +124.0°C)                  

it8716-isa-0228
Adapter: ISA adapter
VCore:       +1.23 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +1.23 V  (min =  +1.28 V, max =  +1.68 V)   ALARM
+3.3V:       +1.79 V  (min =  +2.78 V, max =  +3.78 V)   ALARM
+5V:         +4.87 V  (min =  +4.49 V, max =  +5.48 V)   
+12V:        +4.67 V  (min =  +9.98 V, max = +13.95 V)   ALARM
in5:         +2.50 V  (min =  +0.58 V, max =  +1.34 V)   ALARM
in6:         +1.73 V  (min =  +1.04 V, max =  +1.36 V)   ALARM
5VSB:        +4.76 V  (min =  +4.49 V, max =  +5.48 V)   
VBat:        +3.04 V
fan1:       1397 RPM  (min =   10 RPM)
fan2:          0 RPM  (min =   10 RPM)  ALARM
fan3:          0 RPM  (min =    0 RPM)
temp1:       +60.0°C  (low  = +127.0°C, high = +124.0°C)  sensor = thermal diode
temp2:       +40.0°C  (low  = +127.0°C, high = +124.0°C)  sensor = transistor
temp3:        -9.0°C  (low  = +127.0°C, high = +124.0°C)  sensor = transistor
cpu0_vid:   +0.000 V

```

Note that i am running on a quad core machine (AMD phenom) with an ATI graphics card. So, is that too hot? I also noticed a few alarms there and  i have no-idea what they are about.

Wasn't sure where to post this, if it's in the wrong section feel free to move it ;).

---

### Post by dcstar on 2009-03-07
> **Tulitikku said:**
> I finally got LM-Sensors installed today, i ran a quick check and this is what i got:
               
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +124.0°C)                  

it8716-isa-0228
Adapter: ISA adapter
VCore:       +1.23 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +1.23 V  (min =  +1.28 V, max =  +1.68 V)   ALARM
+3.3V:       +1.79 V  (min =  +2.78 V, max =  +3.78 V)   ALARM
+5V:         +4.87 V  (min =  +4.49 V, max =  +5.48 V)   
+12V:        +4.67 V  (min =  +9.98 V, max = +13.95 V)   ALARM
in5:         +2.50 V  (min =  +0.58 V, max =  +1.34 V)   ALARM
in6:         +1.73 V  (min =  +1.04 V, max =  +1.36 V)   ALARM
5VSB:        +4.76 V  (min =  +4.49 V, max =  +5.48 V)   
VBat:        +3.04 V
fan1:       1397 RPM  (min =   10 RPM)
fan2:          0 RPM  (min =   10 RPM)  ALARM
fan3:          0 RPM  (min =    0 RPM)
temp1:       +60.0°C  (low  = +127.0°C, high = +124.0°C)  sensor = thermal diode
temp2:       +40.0°C  (low  = +127.0°C, high = +124.0°C)  sensor = transistor
temp3:        -9.0°C  (low  = +127.0°C, high = +124.0°C)  sensor = transistor
cpu0_vid:   +0.000 V

```

Note that i am running on a quad core machine (AMD phenom) with an ATI graphics card. So, is that too hot? I also noticed a few alarms there and  i have no-idea what they are about.

Wasn't sure where to post this, if it's in the wrong section feel free to move it ;).

There are default formulas in the sensors package for particular chipsets, motherboard manufacturers use these in many (many) different ways that do not match the default that is installed.

You are free to modify the settings for your detected chipset to match what is actually on your motherboard.

---

### Post by Skripka on 2009-03-07
> **Tulitikku said:**
> I finally got LM-Sensors installed today, i ran a quick check and this is what i got:
    

Note that i am running on a quad core machine (AMD phenom) with an ATI graphics card. So, is that too hot? I also noticed a few alarms there and  i have no-idea what they are about.

Wasn't sure where to post this, if it's in the wrong section feel free to move it ;).

As I recall phenom quads are between 95-125W thermal power, and therefore have a crit temp of around 65C.  They need kept quite cool.

---

### Post by abyrne on 2009-03-07
Some temp sensors in some systems are from random nodes in the firmware of some hardware. Of course, thats only some of them.

 And when it says ALARM it means that it doesn't comply with standard pre-defined by the app. The best way to tell if your sys is too hot is by feeling it (In my opinion).

---

