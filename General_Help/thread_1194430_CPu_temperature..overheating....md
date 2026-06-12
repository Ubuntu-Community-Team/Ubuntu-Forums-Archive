---
title: "CPu temperature..overheating..."
date: 2009-06-22
forum: General Help
---

### Post by akshay.sulakhe on 2009-06-22
Just decided to run a test to see whether my CPU is getting overheated or not..used lm-sensors for that...My machine config...AMD phenom quad core 9950(BE)..Motherboard:- ASUS M3A78-em...and Nvidia 9600gt 512mb..and 2gb 800mhz ddr2 ram...the output of lm sensors was astonishing..i couldnt understand anything..but saw alarm in it...
akshay@Akshay-Desktop:~$ sudo sensors
[sudo] password for akshay: 
it8712-isa-0290
Adapter: ISA adapter
VCore 1:     +1.33 V  (min =  +1.52 V, max =  +3.47 V)   ALARM
VCore 2:     +0.78 V  (min =  +2.10 V, max =  +2.03 V)   ALARM
+3.3V:       +3.33 V  (min =  +1.50 V, max =  +2.11 V)   ALARM
+5V:         +4.30 V  (min =  +0.13 V, max =  +6.45 V)   
+12V:       +12.03 V  (min =  +0.38 V, max =  +5.31 V)   ALARM
-12V:       -15.21 V  (min = -24.41 V, max = -19.26 V)   ALARM
-5V:        -11.22 V  (min =  +0.01 V, max =  -3.04 V)   ALARM
Stdby:       +6.72 V  (min =  +2.28 V, max =  +5.78 V)   ALARM
VBat:        +3.28 V
fan1:       6192 RPM  (min =   18 RPM)
fan2:          0 RPM  (min = 3857 RPM)  ALARM
fan3:          0 RPM  (min =   19 RPM)  ALARM
M/B Temp:    +55.0°C  (low  = +118.0°C, high = +67.0°C)  sensor = thermistor
CPU Temp:    +49.0°C  (low  = +23.0°C, high = -47.0°C)  sensor = thermistor
Temp3:      -128.0°C  (low  = -127.0°C, high =  -3.0°C)  sensor = disabled
cpu0_vid:   +1.550 V

..SO is that a problem..what shud i do...do reply..Thanks...

---

### Post by clonne4crw on 2009-09-28
I would get a new cooler for your CPU. Here are some links for AM2+ heatsinks:

[http://tinyurl.com/yca55p6](http://tinyurl.com/yca55p6)

[http://tinyurl.com/yd8wunl](http://tinyurl.com/yd8wunl)

The only ones I've had personal experience with are the Zalmans, and they do a pretty decent job with my Core 2 Duo e8400.

---

### Post by NullHead on 2009-09-28
I would make sure that your case has good ventilation, that your fans aren't clogged with dust or other debris, and never overclock it.

The temps you listed aren't dangerous yet, but I would also look into a third party cooling solution.

---

### Post by sdowney717 on 2009-10-02
you can run gkrellm to give you a graphical realtime view of your temps and other information

I found you have to run sudo sensors-detect
answer YES to questions, and then reboot to get sudo sensors seeing the sensors.

---

### Post by kavon89 on 2009-10-02
You're not overheating, CPU and Board temps are fine.

```
VCore 1: +1.33 V (min = +1.52 V, max = +3.47 V) ALARM
VCore 2: +0.78 V (min = +2.10 V, max = +2.03 V) ALARM
+3.3V: +3.33 V (min = +1.50 V, max = +2.11 V) ALARM
+5V: +4.30 V (min = +0.13 V, max = +6.45 V)
+12V: +12.03 V (min = +0.38 V, max = +5.31 V) ALARM
-12V: -15.21 V (min = -24.41 V, max = -19.26 V) ALARM
-5V: -11.22 V (min = +0.01 V, max = -3.04 V) ALARM
Stdby: +6.72 V (min = +2.28 V, max = +5.78 V) ALARM
```

Your power supply is poor and doesn't have enough power for your system. Seriously consider replacing this.

```
fan1: 6192 RPM (min = 18 RPM)
fan2: 0 RPM (min = 3857 RPM) ALARM
fan3: 0 RPM (min = 19 RPM) ALARM
```

Two of your fans aren't spinning, and your CPU fan is spinning quite quickly (6k RPM is high while just idling). See if replacing the power supply fixes this since your temperatures are still ok with them not spinning.

---

