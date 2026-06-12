---
title: "Native games with random lags"
date: 2014-01-05
forum: Gaming &amp; Leisure
---

### Post by brunomandaloriano on 2014-01-05
I used to play some games like Penumbra, Amnesia, Costume Quest, Nexuiz, Counter Strike and others without problems just those related with limitations of my hardware.
I was playing Psychonauts and a random lag was occurring at the game, it makes the game unplayable and occurres a lot I just wait some time (from 1 to 8 min) and the game goes normal again, finished the game with this annoying lag and get back to play Costume Quest just to discover the hell's lag was occurring with that game and all games listed in the beginning of the post and also with others like  Left for Dead 2, Brutal Legend and even Super Meat Boy. Firstly I though it could be RAM, but while playing Brutal Legend the lag occurred, checked ram usage and I had more then 1GB available, tried updating Nvidia's drive without success, there are some games that I can play normally, all of them , I think, use less hardware acceleration: JamesTown, Uplink, Cave Story+...

The computer is weak but it have the minimum specs for the games I tried to play:
Ubuntu 13.10 64bit
MB: MSI G31M3-L V2(MS-7529)
CPU: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz
RAM: 4GB (2+2 dual channel) ddr2 800
VGA: GeForce 9500 GT
NVIDIA Driver Version: 331.20.
Linux  3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by kostkon on 2014-01-05
Besides ram usage, have you checked the CPU usage?

---

### Post by R33D3M33R on 2014-01-06
Check CPU and GPU temperatures. You might need to install lm-sensors. Then run: sensors

---

### Post by efflandt on 2014-01-06
Just curious if you had any issues with any of the regular or experimental Ubuntu nvidia drivers before you went xorg.edgers and why you feel you need a cutting edge 331 version with a relatively old model video card?

Since htop or System Monitor CPU percentages do not really tell adaptive CPU speed, I wrote this little shell script to reveal that:```
#!/bin/sh
while [ 1 ]; do
    grep MHz /proc/cpuinfo
    sleep 1
    echo
done
```That may help determine if video may be the bottleneck vs. CPU. Or you could insert an "uptime" command in that loop if not running any "top" to also monitor load ave.

---

### Post by brunomandaloriano on 2014-01-06
Thank you all for replying.

> **kostkon said:**
> Besides ram usage, have you checked the CPU usage?
Yes I've done it before, just measured it again:
While **not lagging** top command showed me the cpu usage was about 30% and the game process marked a maximum of 140% of CPU
While **lagging top** command showed me the cpu usage was about 17,6% and the game process marked a maximum of 100% of CPU

> **R33D3M33R said:**
> Check CPU and GPU temperatures. You might need to install lm-sensors. Then run: sensors

Didn't do it before and I think this could be the cause.
Sensors while **not lagging**:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +93.0°C  (high = +74.0°C, crit = +100.0°C)
Core 1:       +87.0°C  (high = +74.0°C, crit = +100.0°C)
Core 2:       +89.0°C  (high = +74.0°C, crit = +100.0°C)
Core 3:       +93.0°C  (high = +74.0°C, crit = +100.0°C)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.39 V  
in1:          +1.16 V  (max =  +2.04 V)
in2:          +0.91 V  
in3:          +0.72 V  
in4:          +0.96 V  
in5:          +1.09 V  
in6:          +0.87 V  
3VSB:         +3.38 V  
Vbat:         +3.36 V  
fan1:        2912 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:        +81.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +70.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +95.0°C, hyst = +91.0°C)  sensor = thermistor
temp3:        +49.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor
```

Sensors while **lagging**:
```

coretemp-isa-0000coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +83.0°C  (high = +74.0°C, crit = +100.0°C)
Core 1:       +77.0°C  (high = +74.0°C, crit = +100.0°C)
Core 2:       +79.0°C  (high = +74.0°C, crit = +100.0°C)
Core 3:       +82.0°C  (high = +74.0°C, crit = +100.0°C)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.39 V  
in1:          +1.16 V  (max =  +2.04 V)
in2:          +0.91 V  
in3:          +0.72 V  
in4:          +0.94 V  
in5:          +1.09 V  
in6:          +0.88 V  
3VSB:         +3.39 V  
Vbat:         +3.36 V  
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:        +71.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +65.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +95.0°C, hyst = +91.0°C)  sensor = thermistor
temp3:        +50.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

```



> **efflandt said:**
> Just curious if you had any issues with any of the regular or experimental Ubuntu nvidia drivers before you went xorg.edgers and why you feel you need a cutting edge 331 version with a relatively old model video card?

Since htop or System Monitor CPU percentages do not really tell adaptive CPU speed, I wrote this little shell script to reveal that:```
#!/bin/sh
while [ 1 ]; do
    grep MHz /proc/cpuinfo
    sleep 1
    echo
done
```That may help determine if video may be the bottleneck vs. CPU. Or you could insert an "uptime" command in that loop if not running any "top" to also monitor load ave.

I updated the driver because the lags problems started to happen when I was using the 304 version(I think :???:), that was the regular driver of my Ubuntu installation, so I thought that the newest stable version could have a patch for my problem.
Tried the script and the only output I received was: 
cpu MHz        : 2675.784
cpu MHz        : 2675.784
cpu MHz        : 2675.784
cpu MHz        : 2675.784

---

### Post by R33D3M33R on 2014-01-07
If the sensors output is right, then the temperatures are way too high. Your CPU probably hits the temperature limit when gaming, and motherboard slows it down to prevent damage. This causes lag. After it cools for some time, its back to full speed and so on. Clean the dust, open the case and have the box somewhere well ventilated. Maybe even change the thermal paste on the CPU.

---

### Post by brunomandaloriano on 2014-01-10
That's so noob. 
The problem was the dust, blowed the pc and played for 10 hours without the hell's lag. Thanks for the help.

---

