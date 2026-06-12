---
title: "Noobish questions about sensors/screenlets"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by attercop on 2008-03-18
I'll keep this short as i know it's covered a lot, but i may be missing something not in other posts. Here's a screenshot of my desktop:

[http://i14.photobucket.com/albums/a331/xxvm/Screenshot-2.png]("http://i14.photobucket.com/albums/a331/xxvm/Screenshot-2.png")

The screenlet trying to show my CPU temp isn't working correctly like the GPU temp one. I am running 7.10 and have set up sensors. Here is the sensors output:

```
andy@andy-desktop:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +34°C

it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.47 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:   +0.00 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
+3.3V:     +3.28 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:       +4.92 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:     +11.97 V  (min =  +0.00 V, max = +16.32 V)   
-12V:      -4.66 V  (min = -27.36 V, max =  +3.93 V)   
-5V:      -13.64 V  (min = -13.64 V, max =  +4.03 V)   ALARM
Stdby:     +4.92 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:      +3.10 V
fan1:     4017 RPM  (min =  811 RPM, div = 8)          
fan2:        0 RPM  (min =  811 RPM, div = 8)          
fan3:        0 RPM  (min =    0 RPM, div = 8)          
M/B Temp:    +36°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
CPU Temp:    +30°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor   
Temp3:       +31°C  (low  =    -1°C, high =  +127°C)   sensor = thermistor  
```

I'd also like to get the hard drive monitors working correctly, which do after i've viewed them and entered my root pass, but not until. A few tips for editing /etc/fstab without making any security mistakes (regarding permissions) would be very much appreciated.

---

### Post by attercop on 2008-03-20
bump

---

### Post by attercop on 2008-03-23
Bump

---

### Post by psyopper on 2008-03-23
Try posting in the Screenlets section at the Compiz-Fusion forums. The author of those screenlets is there frequently...

[http://forums.compiz-fusion.org](http://forums.compiz-fusion.org)

---

### Post by attercop on 2008-03-24
Ahh. Thanks very much i'll do just that.

---

