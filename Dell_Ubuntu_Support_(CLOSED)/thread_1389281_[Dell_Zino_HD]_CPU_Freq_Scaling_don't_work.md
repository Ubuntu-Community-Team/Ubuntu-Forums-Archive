---
title: "[Dell Zino HD] CPU Freq Scaling don't work"
date: 2010-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Toastie0815 on 2010-01-24
Hi All!

I've hopeless tried to get  CPU Freq Scaling running with my new Zino HD using Ubuntu 9.10 server and generic kernel. :(
The error message says that there is a problem with the BIOS. Do you've seen a similar issue and/or probably have a workaround/solution?

Please find more details from below. I would really appreciate your feedback, even if you say it don't work for you too ;-)


Regards,
Dominik


_There is no cpufreq:_
 ```
ls /sys/devices/system/cpu/cpu0/
 cache  crash_notes  topology
```[U]

Following error message pops up for powernow-k8:[/U]
```
dmesg | grep power
[    1.057713] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual Core Processor 3250e processors (2 cpu cores) (version 2.20.00)
[    1.057731] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.057733] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
```[U]

CPU should support freq scaling:[/U]
```
cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Athlon(tm) X2 Dual Core Processor 3250e
stepping    : 2
cpu MHz        : 1500.156
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips    : 3000.31
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Athlon(tm) X2 Dual Core Processor 3250e
stepping    : 2
cpu MHz        : 1500.156
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips    : 2992.46
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

```_Using 2.6.31-17-server kernel:_
```
uname -a
Linux zino 2.6.31-17-server #54-Ubuntu SMP Thu Dec 10 18:06:56 UTC 2009 x86_64 GNU/Linux
```

---

### Post by Toastie0815 on 2010-01-25
Hi Again!

No one out there also having a Dell Zino with AMD X2 3250e? :confused: I really would like to hear your experience to isolate the issue!

I've tried this afternoon with Ubuntu 8.04 LTS (AMD64) live system -- same issue :( . Tonight I'm going to try with Lucid Lynx, but I don't expect any success. In addition I've placed a [positing in the dell community forum]("http://en.community.dell.com/forums/t/19317855.aspx") as it is most probably no direct Ubuntu related issue.


Regards,
Dominik

---

### Post by Toastie0815 on 2010-01-25
Short update: Also don't work with 2.6.32 kernel :(
There is a [nice description]("http://wejp.k.vu/projects/howto_cnq_athlon_64_x2?lang=de") available how to get powernow also running without support from the bios, but I still hope for a wonder ;-)

---

### Post by Toastie0815 on 2010-03-09
Final update: AMD has confirmed that the Athlon X2 3250e don't support Cool'n'Quite :-(

---

### Post by Kixtosh on 2010-03-09
Toastie, thanks for sharing your experience. Unfortunately, I cannot offer you any additional insight of my own regarding your issue, but could you explain exactly what this new information from AMD means in terms of usability of the Zino HD with Ubuntu? 
 
I've been considering one of these myself (although I've been concerned about the ATI graphics card also).

---

### Post by Toastie0815 on 2010-03-10
> **Kixtosh said:**
> [...], but could you explain exactly what this new information from AMD means in terms of usability of the Zino HD with Ubuntu? 

It means (up to my understanding), that it is not possible to throttle the CPU frequency and voltage, even if the system is in idle (higher temperature / fan noise). As the powernow-k8 module don't load, also monitoring of the CPU is not possible, but I didn't investigated further so far.

The 6850e CPU is probably a better choice, as it seems to have Cool'n'Quite. But I didn't find a user who could confirm this. In addition the total power consumption of the 6850e is higher under load and I don't know if it would be lower in idle with Cool'n'Quite. (The 3250e and 6850e are not available in the open market (at least in Germany), so information about the CPUs is rare.)

If someone has a system with 6850e, please share your experience. :-)

---

### Post by Kixtosh on 2010-03-10
OK, thanks for the information. I'm hesitating between the Zino, the Zotac MAG, and some of the other options out there (Acer and Eee PC).

---

### Post by reiki on 2010-03-11
I have the 6850 processor. I have not noticed any fan noise at all actually and I've left the machine running for 2 or 3 days. 

Is there something you'd like me to run on it to check what you're looking for? I have Karmic running on the Zino HD with no real problems. I have the HD4330 card, integrated sound, 8GB memory, e6850 processor, 750GB hard drive.

I have Windows7 in a 100GB partition and installed Ubuntu to take up the rest except for 100GB unallocated in case I want to try another Ubuntu version :)

---

### Post by Toastie0815 on 2010-03-11
> **reiki said:**
> I have the 6850 processor. I have not noticed any fan noise at all actually and I've left the machine running for 2 or 3 days. 

Is there something you'd like me to run on it to check what you're looking for? I have Karmic running on the Zino HD with no real problems. I have the HD4330 card, integrated sound, 8GB memory, e6850 processor, 750GB hard drive. [...]

Great! Would be very nice if you could post the output of following commands:
```
dmesg | grep power
``````
ls /sys/devices/system/cpu/cpu0/
```Is the fan really not running at all when the system is in idle? My Zino HD is so loud that it would not be possible to sleep next to. ;-) There is also a recording of the fan sound on YouTube [http://www.youtube.com/watch?v=UxGtm_OMObI](http://www.youtube.com/watch?v=UxGtm_OMObI) (not from me).

If you have a "power-meter" available, it would also be interesting how many watts it takes during idle. (My box with 3250e needs about 30 watt.)

---

### Post by Toastie0815 on 2010-03-11
> **Kixtosh said:**
> OK, thanks for the information. I'm hesitating between the Zino, the Zotac MAG, and some of the other options out there (Acer and Eee PC).

You may also check following thread including interesting information about the Zino HD:
[http://ubuntuforums.org/showthread.php?t=1339404&highlight=dell+zino&page=5](http://ubuntuforums.org/showthread.php?t=1339404&highlight=dell+zino&page=5)
(I've also outlined there the alternatives I've considered.)

---

### Post by reiki on 2010-03-11
> **Toastie0815 said:**
> Great! Would be very nice if you could post the output of following commands:
```
dmesg | grep power
``````
ls /sys/devices/system/cpu/cpu0/
```Is the fan really not running at all when the system is in idle? My Zino HD is so loud that it would not be possible to sleep next to. ;-) There is also a recording of the fan sound on YouTube [http://www.youtube.com/watch?v=UxGtm_OMObI](http://www.youtube.com/watch?v=UxGtm_OMObI) (not from me).

If you have a "power-meter" available, it would also be interesting how many watts it takes during idle. (My box with 3250e needs about 30 watt.)
OK... pasting...
```

yardbird@bigbird:~$ dmesg | grep power
[    1.007304] powernow-k8: Found 1 AMD Athlon(tm) Neo X2 Dual Core Processor 6850e processors (2 cpu cores) (version 2.20.00)
[    1.007360] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x16
[    1.007363] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x1e
[   14.181402]    groups: 0-1 (__cpu_power = 2048)
[   14.181420]    groups: 0-1 (__cpu_power = 2048)
yardbird@bigbird:~$ 

```
and
```

yardbird@bigbird:~$ ls /sys/devices/system/cpu/cpu0/
cache  cpufreq  crash_notes  topology
yardbird@bigbird:~$ 

```

As far as the fan.... it's so quiet I hear the hard drive over the fan. The fan is barely audible.

that help?  I'll see if I can get temps...
```

yardbird@bigbird:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +38.0°C                                    
Core0 Temp:  +43.0°C                                    
Core1 Temp:  +42.0°C                                    
Core1 Temp:  +35.0°C                                    

f71858fg-isa-0a00
Adapter: ISA adapter
in0:         +1.66 V
in1:         +1.67 V
in2:         +1.64 V
fan1:       1997 RPM
fan2:       2590 RPM
fan3:          0 RPM  ALARM
temp1:       +52.5°C  (high = +70.0°C, hyst = +60.0°C)  
temp2:       +38.2°C  (high = +100.0°C, hyst = +85.0°C)  sensor = transistor
temp3:       +46.6°C  (high = +100.0°C, hyst = +85.0°C)  

yardbird@bigbird:~$ 

```

best I can do on short notice. :) I don't have a power meter.

---

### Post by Toastie0815 on 2010-03-12
> **reiki said:**
> 
OK... pasting...
[...] 
As far as the fan.... it's so quiet I hear the hard drive over the fan. The fan is barely audible.

that help?  I'll see if I can get temps...
[...]
best I can do on short notice. :) I don't have a power meter.

reiki, thanks a lot for the clarification, that helped a lot!
Based  on your posting I really consider to buy a machine with 6850e and sell the 3250e box on eBay ;)

Regarding the HDD, you may change the acoustic management settings with the respective vendor tool. (This may lower the disk performance.)

---

### Post by reiki on 2010-03-12
Toastie0815,

If you get one with a loud fan.... 2 things to check...

#1 is the fan secured properly in the case. There have been reports of some fans with loose screws.

#2 call Dell tech support and have them replace the fan. It should be whisper quiet even under heavy load. It should not "spin up" like some laptop fans I've heard. This box is EXTREMELY quiet when it's running properly.

---

