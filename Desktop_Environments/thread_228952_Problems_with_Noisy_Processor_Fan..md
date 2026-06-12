---
title: "Problems with Noisy Processor Fan."
date: 2006-08-03
forum: Desktop Environments
---

### Post by mistapotta on 2006-08-03
I recently built a computer with an Intel D945Gcz motherboard and an Intel Pentium-D 3.0 processor, and the fan sounds like a vacuum cleaner.  I'd like to find a way to regulate the fan speed, as other operating systems seem to be able to do it.

I installed lm-sensors as shown [here]("http://ubuntuforums.org/showthread.php?t=2780") and got an output from it:

```
lm85-i2c-0-2e
Adapter: SMBus I801 adapter at 2000
V1.5:       +1.58 V  (min =  +1.42 V, max =  +1.58 V)
VCore:      +1.25 V  (min =  +1.76 V, max =  +1.95 V)   ALARM
V3.3:       +3.33 V  (min =  +3.13 V, max =  +3.47 V)
V5:        +5.10 V  (min =  +4.74 V, max =  +5.26 V)
V12:      +12.19 V  (min = +11.38 V, max = +12.62 V)
CPU_Fan:   5268 RPM  (min = 1000 RPM)
fan2:         0 RPM  (min =    0 RPM)
fan3:         0 RPM  (min =    0 RPM)
fan4:         0 RPM  (min =    0 RPM)
CPU:         +39Â°C  (low  =   +10Â°C, high =   +60Â°C)
Board:       +30Â°C  (low  =   +10Â°C, high =   +35Â°C)
Remote:      +34Â°C  (low  =   +10Â°C, high =   +35Â°C)
CPU_PWM:   255
Fan2_PWM:  255
Fan3_PWM:  255
vid:      +1.850 V  (VRM Version 9.1)
```

I've tried following through the explanation [here]("http://ubuntuforums.org/showthread.php?t=42737") but haven't had any success.  In particular, when I try to add

```
set fan1_div 4
```

as specified, I get

```
~$ sudo sensors -s
Error: Line 2196: Unknown feature name
lm85-i2c-0-2e: No such feature known
```

I understand there are situations where my fan would need to run near 5300 RPM, but the baby in the next room does need to sleep.  

Anyone have any ideas?

~Tony David Potter

---

