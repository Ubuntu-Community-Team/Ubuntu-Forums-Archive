---
title: "Powernowd reports 1.5Ghz but I'm on a 2Ghz Celeron?"
date: 2005-12-09
forum: General Help
---

### Post by zi99y on 2005-12-09
Hi All, any help with this is much appreciated:

I had problems getting cpu scaling working until I read [this thread]("http://ubuntuforums.org/showthread.php?t=84604&highlight=cpufreq-selector") which I then ran sudo dpkg-reconfigure gnome-applets, and answered yes to setting the suid of the cpufreq-selector. Then to my delight the gnome panel cpu frequency monitor worked! But it lists the maximum speed as being 1.5Ghz.

```
cat /proc/cpuinfo
```clearly says I'm on a Intel(R) Pentium(R) M processor 2.00GHz - which is as the label on my laptop also confirms.

also...
```
$ sudo powernowd
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
powernowd:   cpu0: 187Mhz - 1500Mhz (8 steps)

```

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
```shows the values: 187500 375000 562500 750000 937500 1125000 1312500 1500000 

Does that mean I can add 2000000 to this list to make my machine run at its maximum speed?

Any words of wisdom on this from our resident Ubuntians? 

cheers

---

### Post by Jormundgand on 2005-12-09
Intel processors in general are extremely sloppy with their cycles and so perform less quickly than similarly-clocked AMD processors. My Athlon is classed as an AMD Athlon XP 2200+, meaning it outperforms a 2.2GHz Pentium 4. I imagine powernowd sees through this folly to the true processing power of your Celeron.

---

### Post by zi99y on 2005-12-09
Interesting.... But I confess I called it a celeron by mistake and it is in fact a brand new Centrino dothan - Pentium M 760. Does this make a difference?

---

### Post by matthew on 2005-12-09
[quote=zi99y]Interesting.... But I confess I called it a celeron by mistake and it is in fact a brand new Centrino dothan - Pentium M 760. Does this make a difference?[/quote]I can't answer as to why this is happening or what to do about it. I do think you should be getting accurate figures, not what you have here. I have a dothan Pentium M 745. Here is my data for comparison.

```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.80GHz
stepping        : 6
cpu MHz         : 598.290
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 1185.10

``` ```
$ sudo powernowd
Password:
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
powernowd:   cpu0: 600Mhz - 1800Mhz (7 steps)
``` ```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1800000 1600000 1400000 1200000 1000000 800000 600000

```
So, yes. You do seem to have a problem. My uneducated thought is that you should be able to edit as you mentioned and have it work, but I'm not willing to go out on a limb and say for certain that will make it work--I just don't have experience with that. If it were my computer I would try it and see (after making a good backup of the original file so I could boot in recovery mode and restore it if it didn't work), knowing that I was taking a little bit of a risk. Note: I don't know that this could actually cause any damage to your processor, but ???

---

