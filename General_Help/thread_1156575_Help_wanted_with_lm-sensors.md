---
title: "Help wanted with lm-sensors"
date: 2009-05-11
forum: General Help
---

### Post by Milambar on 2009-05-11
I installed lm-sensors today, and ran sensors-detect, and made the requested changes to /etc/modules that sensors-detect asks you to make. However, the output of sensors is.. non-sensical. The output is below.

```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +124.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +6.0°C                                    
Core0 Temp:   -2.0°C                                    
Core1 Temp:   +5.0°C                                    
Core1 Temp:   +1.0°C                                    

it8716-isa-0290
Adapter: ISA adapter
VCore:       +1.09 V  (min =  +0.00 V, max =  +4.08 V)   
VDDR:        +2.50 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +1.79 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +5.54 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:       +11.71 V  (min =  +0.00 V, max = +16.32 V)   
in5:         +1.17 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +2.83 V  (min =  +0.00 V, max =  +4.08 V)   
5VSB:        +4.97 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:        +2.99 V
fan1:       2518 RPM  (min =    0 RPM)
fan2:        894 RPM  (min =    0 RPM)
temp1:        +2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp2:       +42.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +25.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor

```

Its non-sensical because I have a dual-core CPU and yet it lists 4 different temps, and none of them are even close. I mean, they are all below 10C for an AMD 64bit X2 4400+.

Also, it doesn't show my GPU temp or my HDD temp.

The machine specifications are:

Motherboard: MCP61PM-HM (Nettle2)
CPU: AMD 64bit X2 4400+
HDD: 2 of them, 1-ide, the other SATA. Make: Unknown.
Graphics Card: nVidia 8600GT

I hope someone can point me in the right direction with getting sensors working properly, or at least, making some sense.

---

