---
title: "Need help pulling info from sensors output"
date: 2009-03-24
forum: Desktop Environments
---

### Post by wolfe on 2009-03-24
I need to pull the temperature from the k10temp line and have no idea how to do it.  my current script pulls the "virtual device"

```
pwolfe@omniscience:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +35.0°C  (crit = +84.0°C)                  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +42.5°C                                    

it8716-isa-0228
Adapter: ISA adapter
VCore:       +1.50 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +1.30 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +4.97 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:       +12.03 V  (min =  +0.00 V, max = +16.32 V)   
in5:         +1.20 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +2.11 V  (min =  +0.00 V, max =  +4.08 V)   
5VSB:        +4.89 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:        +3.36 V
fan1:          0 RPM  (min = 3245 RPM)
fan2:          0 RPM  (min = 3245 RPM)
fan3:          0 RPM  (min = 3245 RPM)
temp1:       +34.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermal diode
temp2:       +33.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermistor
temp3:       +36.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermistor
cpu0_vid:   +0.763 V

pwolfe@omniscience:~$ 

```

---

### Post by Bachstelze on 2009-03-24
```
sensors | head -n 7 | tail -n 1 | awk '{print $2}'
```

[font="monospace"]head -n 7[/font] prints only the first 7 lines,
[font="monospace"]tail -n 1[/font] prints only the last line, and
[font="monospace"]awk '{print $2}'[/font] prints only the second word.

So all those commands run in a sequence print only the second word of the last of the first 7 lines (i.e. the 7th line).

---

### Post by wolfe on 2009-03-24
Thats great, and it displays just as I want it to, but it also seems to block anything else in my conkyrc from displaying.

```
CPU Temp: ${alignr}${execi 1 sensors | head -n 7 | tail -n 1 | awk '{print $2}'
```

---

### Post by m_duck on 2009-03-24
You need the closing curly brace on the end of the line```
[FONT=monospace]CPU Temp: ${alignr}${execi 1 sensors | head -n 7 | tail -n 1 | awk '{print $2}'}[/FONT]
```At least, I ***think*** that should do it.

---

### Post by wolfe on 2009-03-24
ya that does it, and I see why now.  Thanks for the explanations guys, but now it is SLOW.  I looks like conky updates every 5 secs now as opposed to 0.5

I ran conky from the command line, and I dont see any output there to suggest it being so slow

EDIT:  After I posted this, I noticed updates available, mostly kernel updates.  Upon restarting, the issue seems resolved.  Thanks for the help guys!

---

