---
title: "Possible Bug: Ksysguard in Hardy broken?"
date: 2008-06-04
forum: Desktop Environments
---

### Post by goldix on 2008-06-04
Hi,

I did a fresh install of hardy after my PC didn't boot anymore after the upgrade from feisty to hardy.

However, ksysguard doesn't show my mainboard, CPU, etc temperature anymore in hardy (worked in feisty). lmsensors with it's kernel module works fine, sensors are detected perfectly:

-------------
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +57.0°C

it87-isa-0290
Adapter: ISA adapter
VCore 1:     +1.52 V  (min =  +0.00 V, max =  +4.08 V)
VCore 2:     +1.47 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.30 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +5.11 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +11.90 V  (min =  +0.00 V, max = +16.32 V)
-12V:       -20.00 V  (min = -27.36 V, max =  +3.93 V)
-5V:         -2.49 V  (min = -13.64 V, max =  +4.03 V)
Stdby:       +5.03 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +0.00 V
fan1:          0 RPM  (min =    0 RPM, div = 16)
fan2:          0 RPM  (min =    0 RPM, div = 16)
fan3:       2280 RPM  (min =    0 RPM, div = 8)
M/B Temp:    +45.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
CPU Temp:    +71.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
Temp3:       +56.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = transistor
-------------

Just the "Hardware Sensors" tab in ksysguard disappeared in hardy. Same problem on another machine running hardy.

There also was a bug in Suse a couple of weeks ago, where the "Hardware Sensors" tab also didn't show up, but that was fixed after a couple of days - might this be related to this Ubuntu Bug as well?

Can any KDE user confirm this?

Cheers,

Markus.

---

### Post by mo0n_sniper on 2008-08-15
Same problem here

---

