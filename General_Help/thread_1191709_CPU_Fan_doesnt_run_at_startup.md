---
title: "CPU Fan doesnt run at startup"
date: 2009-06-19
forum: General Help
---

### Post by The Real Dave on 2009-06-19
Ok, so since my CPU temp was getting too high for my like (PIV 3Ghz, 50 at idle, 60-65 under load), I purchsed a new fan case (a large 120mm), and thorughly cleaned the computer from top to bottom. It hadn't been cleaned fully since its purchase in 06, and the dust that came out of the heatsink was scary :lolflag: 

So this new fan is mounted on the side of the case, blowing air down on the mobo and heatsink. Now at idle the CPU is around 40C and 50C under load. 

But here's my problem. At startup, my two case fans spin up, but the CPU fan doesn't. In fact, it doesn't start to spin until the CPU goes over 35C, and then only spins are 700-850 rpm (it had been working constantly at 4500rpm) Now I know that my chip is cool enough without the fan until I start putting it under pressure, but a I'd feel much better if it was at least spinning to some degree. 

I've looked through BIOS, and couldn't find anything there, so can anyone advise me on what to do, or point me to a relevant page? 

Or is it fine how it is, not spinning at startup?

Thanks in advance =]


Output of CPU info
```
dave@Ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.93GHz
stepping	: 1
cpu MHz		: 2925.519
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
bogomips	: 5851.03
clflush size	: 64
power management:

```

lm-sensors at idle
```
dave@Ubuntu:~$ sensors
it8712-isa-0a10
Adapter: ISA adapter
VCore 1:     +1.34 V  (min =  +0.00 V, max =  +4.08 V)   
VCore 2:     +1.22 V  (min =  +0.00 V, max =  +4.08 V)   
+3.3V:       +3.30 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +5.00 V  (min =  +0.00 V, max =  +6.85 V)   
+12V:       +11.84 V  (min =  +0.00 V, max = +16.32 V)   
-12V:       -13.74 V  (min = -27.36 V, max =  +3.93 V)   
-5V:         +0.35 V  (min = -13.64 V, max =  +4.03 V)   
Stdby:       +4.97 V  (min =  +0.00 V, max =  +6.85 V)   
VBat:        +3.17 V
fan1:        795 RPM  (min =    0 RPM, div = 8)
fan2:          0 RPM  (min =    0 RPM, div = 8)
fan3:       1339 RPM  (min =    0 RPM, div = 8)
M/B Temp:    +26.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermistor
CPU Temp:    +40.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = thermal diode
Temp3:      -128.0°C  (low  =  -1.0°C, high = +127.0°C)  sensor = disabled
cpu0_vid:   +0.863 V

```

Fan 1 is the CPU, Fan 3 is the 120mm case fan. I also have an 80mm fan at the rear of the case, which doesn't contain a sensor

---

### Post by redilyn on 2009-06-19
Really it is probably fine the way it is. 35C is pretty cool for a cpu.

If you are not comfortable with the fan not running you may want to check out this thread

[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)

---

### Post by The Real Dave on 2009-06-19
Thanks for the link =]

---

### Post by JKyleOKC on 2009-06-19
You might look into replacing that CPU fan. These tiny things have to run at high speed to move any effective amount of air, and the slow start you describe sounds an awfully lot like clogged-up bearings. If you have pets, especially long-haired ones, the fans may well have developed built-in "brake pads" from compacted pet hair! I have to replace fans every year or two, here, because of this...

---

### Post by SerenityKill3r on 2009-06-19
You could always connect the fan straight to the power supply. All my fans run at 100% all the time, thats 5 case fans, 1 CPU fan and one GPU fan (which runs at 60%).

---

### Post by The Real Dave on 2009-06-19
> **JKyleOKC said:**
> You might look into replacing that CPU fan. These tiny things have to run at high speed to move any effective amount of air, and the slow start you describe sounds an awfully lot like clogged-up bearings. If you have pets, especially long-haired ones, the fans may well have developed built-in "brake pads" from compacted pet hair! I have to replace fans every year or two, here, because of this...

Ya, I will look into changing it, its a generic 90mm fan, so I'd look into a quieter one. I was planning to change to a bigger heatsink, but the temp improvement I got after a good clean and a new case fan, the 120mm, has made me think twice. 40C seems a good kind of a temp for a PIV. Also, space around my current heatsink is tight, as the graphics chip's heatsink is right next to it :confused:

I dont have pets to clog it, but then again, the heatsink hadn't been cleaned since I bought it in 06. 

Also, I was thinking of changing the thermal grease to something like Antec Silver, or better. Is it worth it?

---

### Post by Yellow Pasque on 2009-06-19
Arctic Silver's good stuff. I use it in all of my high-powered CPU builds.

For fan control on a desktop, use:
```
sudo pwmconfig
```

---

### Post by The Real Dave on 2009-06-19
> **Temüjin said:**
> Arctic Silver's good stuff. I use it in all of my high-powered CPU builds.

For fan control on a desktop, use:
```
sudo pwmconfig
```

Thanks =] Just what I was looking for, however, after setting it up, and trying to go back in an fix an error, I get this;

```
dave@Ubuntu:~$ sudo pwmconfig
File /var/run/fancontrol.pid exists. This typically means that the
fancontrol deamon is running. You should stop it before running pwmconfig.
If you are certain that fancontrol is not running, then you can delete
/var/run/fancontrol.pid manually.

```

Anyone know how I can stop the deamon? Or can I just delete the file?

---

### Post by Yellow Pasque on 2009-06-19
Maybe something like:
```
sudo /etc/init.d/fancontrol stop
```

---

### Post by The Real Dave on 2009-06-20
Thanks guys =] That sorted it nicely.

---

