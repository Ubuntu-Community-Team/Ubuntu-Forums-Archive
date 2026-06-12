---
title: "CPU temp ERROR"
date: 2009-03-25
forum: General Help
---

### Post by lies on 2009-03-25
I just did what's in this page : 
[http://www.compdigitec.com/labs/2008/07/18/measure-cpu-temp-in-ubuntu/](http://www.compdigitec.com/labs/2008/07/18/measure-cpu-temp-in-ubuntu/)

And got this :

benjamin@benjamin-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +12.0°C                                    
Core0 Temp:  +13.0°C                                    
Core1 Temp:  +16.0°C                                    
Core1 Temp:   +5.0°C                                    

My system : AMD 5050e, ASUS M3A78-EM, Ubuntu 8.10.

Im sure that's not possible because i remember the temps in windows were 38C and 36C; and there are only 2 cores, where are the other temp readings coming from?

---

### Post by lies on 2009-03-25
Help plz....

---

### Post by lies on 2009-03-25
I typed "sensors" in the terminal again and now i got this : 

benjamin@benjamin-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +12.0°C                                    
Core0 Temp:  +13.0°C                                    
Core1 Temp:  +17.0°C                                    
Core1 Temp:   +7.0°C                                    

it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.28 V  (min =  +0.21 V, max =  +0.72 V)   ALARM
VCore 2:     +0.00 V  (min =  +0.00 V, max =  +0.03 V)   ALARM
+3.3V:       +3.22 V  (min =  +0.16 V, max =  +2.30 V)   ALARM
+5V:         +0.99 V  (min =  +0.00 V, max =  +3.49 V)   
+12V:       +12.74 V  (min =  +0.51 V, max =  +0.00 V)   ALARM
-12V:       -15.58 V  (min = -27.11 V, max = -27.11 V)   ALARM
-5V:         -3.46 V  (min =  -4.77 V, max = -12.81 V)   ALARM
Stdby:       +0.89 V  (min =  +0.05 V, max =  +0.97 V)   
VBat:        +3.26 V
fan1:       2922 RPM  (min =   19 RPM)
fan2:          0 RPM  (min = 61363 RPM)  ALARM
fan3:          0 RPM  (min = 84375 RPM)  ALARM
M/B Temp:    +40.0°C  (low  =  +0.0°C, high = +12.0°C)  sensor = transistor
CPU Temp:    +39.0°C  (low  =  +0.0°C, high = -119.0°C)  sensor = transistor
Temp3:      +128.0°C  (low  =  +8.0°C, high =  +0.0°C)  sensor = disabled
cpu0_vid:   +1.550 V

---

### Post by 3Miro on 2009-03-25
I have found the information from sensors to be very unreliable. I don't know what the problem is.

---

### Post by lies on 2009-03-26
yeah, right...

---

### Post by dcstar on 2009-03-26
> **lies said:**
> I typed "sensors" in the terminal again and now i got this : 

benjamin@benjamin-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +12.0°C                                    
Core0 Temp:  +13.0°C                                    
Core1 Temp:  +17.0°C                                    
Core1 Temp:   +7.0°C                                    

it8712-isa-0290
......
**CPU Temp:    +39.0°C  (low  =  +0.0°C, high = -119.0°C)  sensor = transistor**
Temp3:      +128.0°C  (low  =  +8.0°C, high =  +0.0°C)  sensor = disabled
cpu0_vid:   +1.550 V

You have a reliable CPU temp there, use it.

---

### Post by lies on 2009-03-26
Then, what can you tell me about the CPU voltage and the other "core" temps?

I want my pc to be windows-free, i already have the apps I need, I don't care about the games, I only need my pc to be stable.

---

### Post by miegiel on 2009-03-30
Here's my sensors output. If I compare these temps with those in my BIOS then temp1 of the it8716-isa-0228 sensor is my real cpu temp.

To detect more sensors run ```
sensors-detect
``` 

BTW I'm trying to figure out why the k8temp-pci-00c3 sensor readout is to low. If anyone has any ideas on this .... :D

```
:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +42.0°C                                    
Core0 Temp:  +48.0°C                                    
Core1 Temp:  +41.0°C                                    
Core1 Temp:  +47.0°C                                    

it8716-isa-0228
Adapter: ISA adapter
VCore:       +1.33 V  (min =  +0.00 V, max =  +3.95 V)
VDDR:        +1.28 V  (min =  +3.06 V, max =  +4.08 V)
+3.3V:       +3.31 V  (min =  +3.54 V, max =  +1.52 V)
+5V:         +4.95 V  (min =  +5.99 V, max =  +4.06 V)
+12V:       +12.03 V  (min = +16.19 V, max = +16.32 V)
in5:         +1.18 V  (min =  +4.02 V, max =  +4.08 V)
in6:         +2.30 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:        +4.87 V  (min =  +3.25 V, max =  +6.80 V)
VBat:        +3.33 V
fan1:       1785 RPM  (min = 3245 RPM)
fan2:          0 RPM  (min = 3245 RPM)
fan3:          0 RPM  (min = 3245 RPM)
temp1:       +58.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = thermal diode
temp2:       +44.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = transistor
temp3:       +53.0°C  (low  = +127.0°C, high = +84.0°C)  sensor = transistor
cpu0_vid:   +1.550 V

```

---

### Post by NickD-NLUG on 2009-06-13
These sensors appear to be suspect, see:

[http://www.lm-sensors.org/ticket/2278](http://www.lm-sensors.org/ticket/2278)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209670](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209670)

Therefore developers won't be trying to fix this issue as the output from the sensors isn't reliable enough.

---

### Post by dcstar on 2009-06-13
> **NickD-NLUG said:**
> These sensors appear to be suspect, see:

[http://www.lm-sensors.org/ticket/2278](http://www.lm-sensors.org/ticket/2278)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209670](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209670)

Therefore developers won't be trying to fix this issue as the output from the sensors isn't reliable enough.

I cannot believe the ignorance that is surrounding these bugs, it (should be) well known that AMD keep changing the way their various different CPU builds output the CPU core temp values - the "Brisbane" die X2-64 CPUS put out values far different from the previous die, but you can still drop them into the same motherboard (I know because I upgraded to one of these).

The problem is the software developers do not/can not keep up with all the changes the CPU hardware manufactures throw around, and that is why people are **told **to use the motherboard data.

---

### Post by miegiel on 2009-06-14
> **dcstar said:**
> I cannot believe the ignorance that is surrounding these bugs, ...

Thanks for reducing my ignorance ;)

---

### Post by NickD-NLUG on 2009-06-20
> **dcstar said:**
> I cannot believe the ignorance that is surrounding these bugs, it (should be) well known that AMD keep changing the way their various different CPU builds output the CPU core temp values - the "Brisbane" die X2-64 CPUS put out values far different from the previous die, but you can still drop them into the same motherboard (I know because I upgraded to one of these).

The problem is the software developers do not/can not keep up with all the changes the CPU hardware manufactures throw around, and that is why people are **told **to use the motherboard data.

Any tips on an appropriate offset to use so that these values can be more accurate... or at least close enough so that I can spot if a temperature is too hot.

Occasionally they've seemed to give a more appropriate value, around forty degrees C, but I'm trying to collate log entries about that.

---

