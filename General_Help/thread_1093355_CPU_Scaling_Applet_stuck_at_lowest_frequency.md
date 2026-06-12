---
title: "CPU Scaling Applet stuck at lowest frequency"
date: 2009-03-11
forum: General Help
---

### Post by Haluci on 2009-03-11
I'm running a Core 2 Duo processor clocked at 2GHz.  Usually, I have the frequency scaling applet running in "Conservative" mode, and this works well at keeping my laptop (an Inspiron E1405) with a good battery life.  Recently, the CPU scaling monitor seems stuck at 1GHz.  When I open the menu of the applet and pick a mode, it seems to be selected but the frequency icon stays at 1GHz (even when I select "Performance" mode!)  When I pick a specific frequency above 1GHz, 1GHz ends up being the frequency being selected no matter which frequency I click.  So, everything I do is now quite slow.  Does anybody know what might be causing this?

Thanks! :)

---

### Post by linuxuser21 on 2009-03-11
Is it running at that or does it just say that it is?

---

### Post by Haluci on 2009-03-11
> **linuxuser21 said:**
> Is it running at that or does it just say that it is?

It's running this way.  No matter what mode or frequency I select, running cat /proc/cpuinfo gives me this:

```
$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping	: 6
**cpu MHz		: 1000.000**
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3989.96
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping	: 6
**cpu MHz		: 1000.000**
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3990.03
clflush size	: 64
power management:

```

I'll try rummaging through my BIOS to see if something got borked.

---

### Post by smileboot on 2009-04-30
Having this exact same issue on a pentium M chip. Anyone solve this problem or know whats causing it?

---

### Post by rainwalker on 2009-05-13
Same problem here, stuck at 600 MHz with a 1700 MHz Pentium M. The CPU frequency scaling monitor I added to the panel seemed to work at first, letting me push it up to 1700 MHz, but then it reverted back to 600 and won't let me change it. No matter what I click, it sticks at 600 MHz. I've given it admin priviliges, installed every possible power management package I could think of (a few threads seemed to indicate that installing "powernowd" fixed it, and it seemed to but then reverted back to 600 MHz again).

---

### Post by jaymode on 2009-05-24
Also having this issue on Ubuntu 9.04. I have placed my information in the following bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/324211)

Please add your information if possible.

---

### Post by Aped on 2009-05-24
Same issue, 9.04. 

1600 intel M, capped at 600mhz. 

Would LOVE to hear a fix for this.

---

### Post by jaymode on 2009-05-25
> **Aped said:**
> Same issue, 9.04. 

1600 intel M, capped at 600mhz. 

Would LOVE to hear a fix for this.



So my "fix" to get my processors to run at the fastest possible speed was to edit my /boot/grub/menu.lst file and append "acpi=off" to my kernel line. However, this disabled all cpu scaling and other ACPI related items.

Can you please post your issue/findings to the bug report I had mentioned in the previous post?

---

### Post by Aped on 2009-05-25
> **jaymode said:**
> So my "fix" to get my processors to run at the fastest possible speed was to edit my /boot/grub/menu.lst file and append "acpi=off" to my kernel line. However, this disabled all cpu scaling and other ACPI related items.

Can you please post your issue/findings to the bug report I had mentioned in the previous post?

I don't have a launchpad account (I know, I know) but I'll make one I guess, if only to sign your epetition, it's a good cause. 

I don't even use a scaling applet or whatever, my dumb CPUs just seem to be firing on half or fewer pistons. Maybe auto-throttling due to heat?

---

### Post by Aped on 2009-05-26
> **jaymode said:**
> ...However, this disabled all cpu scaling and other ACPI related items....

lol yeah like Hibernating. sigh, not going to work for me.

---

### Post by dpsleep on 2009-05-26
can somone post the output of both

cat /proc/acpi/processor/C000/*
and 
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq

---

### Post by Aped on 2009-05-27
> **dpsleep said:**
> can somone post the output of both

cat /proc/acpi/processor/C000/*
and 
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
Sure. 

I assume CPU0/ will do in place of C000/, since I don't have one o dem. 
```

:~$ cat /proc/acpi/processor/CPU0/*
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 2000000000 usec
states:
    C1:                  type[C1] promotion[--] demotion[--] latency[001] usage[00000007] duration[00000000000000000000]
    C2:                  type[C2] promotion[--] demotion[--] latency[001] usage[00256318] duration[00000000003473482385]
    C3:                  type[C3] promotion[--] demotion[--] latency[085] usage[00045099] duration[00000000000068009037]
    C4:                  type[C3] promotion[--] demotion[--] latency[185] usage[01161510] duration[00000000015357449132]
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

And for the second bit of info: 
```

:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
1600000

```

CPUinfo still says 1.6GHz under model name and 600MHz under processor speed; disabling ACPI *does* change this to proper values, but it also has some deleterious effects on my poor little laptop too, seems to make stuff run oddly.

---

### Post by jaymode on 2009-05-27
I will try to post my info when I get back home and can get it off of my desktop.

---

### Post by schmolch on 2009-05-29
Same problem here on a CoreDuo running 9.10

---

### Post by Yellow Pasque on 2009-05-29
See if your settings are being overridden by the cpufreq daemon. If they are, you can control the dameon with the config file in /etc

---

### Post by schmolch on 2009-05-29
> **Temüjin said:**
> See if your settings are being overridden by the cpufreq daemon. If they are, you can control the dameon with the config file in /etc

Its configured for Performance mode there but performance mode never kicks in.

---

### Post by andreselsuave on 2009-05-30
the applet is not working for me neither... any1 have a solution yet? Im running ubuntu 9.04 on a hp 8710p laptop

thankyou

---

### Post by jaymode on 2009-06-01
Here is the info I promised earlier:
```
$ cat /proc/acpi/processor/CPU0/*
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no
<not supported>
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 2000000000 usec
states:
<not supported>

```

```
cat /proc/acpi/processor/CPU1/*
processor id:            1
acpi id:                 1
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no
<not supported>
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 2000000000 usec
states:
<not supported>

```

```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq 
2500000
$ cat /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_max_freq 
2500000

```

```
$ cpufreq-info 
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1.50 GHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.00 GHz, 1.50 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.50 GHz and 1.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.50 GHz.
  cpufreq stats: 2.50 GHz:0.10%, 2.00 GHz:0.14%, 1.50 GHz:99.77%  (2)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1.50 GHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.00 GHz, 1.50 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.50 GHz and 2.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.50 GHz.
  cpufreq stats: 2.50 GHz:0.51%, 2.00 GHz:0.01%, 1.50 GHz:99.48%  (41)


```

---

### Post by andreselsuave on 2009-06-02
Is there a way to change the CPU frequency using the terminal? That way I could know if my problem is related to the applet...

Ok, I figured it out: 

 sudo cpufreq-set -f 2201000

it works for me. I think the problem is related to the applet. dpkg-reconfigure gnome-applets didn't work for me. Well, it does sometimes, but it it goes away again :/ I hope they fix this

---

### Post by jaymode on 2009-06-02
> **andreselsuave said:**
> Is there a way to change the CPU frequency using the terminal? That way I could know if my problem is related to the applet...

Ok, I figured it out: 

 sudo cpufreq-set -f 2201000

it works for me. I think the problem is related to the applet. dpkg-reconfigure gnome-applets didn't work for me. Well, it does sometimes, but it it goes away again :/ I hope they fix this

I had tried that but it doesn't work for me and I also had the same issue in the Fedora 11 preview.

---

### Post by andreselsuave on 2009-06-03
Thought it had worked, but it hasn't ... 

I unplugged the AC cord and now I can't set the cpu frequency, not with the applet nor with the terminal command... maybe it is a powernowd bug, but cpufreqd doesnt work for me. I have a HP8710p laptop, im not sure, but I think the processors are Intel

---

### Post by jaymode on 2009-06-03
> **andreselsuave said:**
> Thought it had worked, but it hasn't ... 

I unplugged the AC cord and now I can't set the cpu frequency, not with the applet nor with the terminal command... maybe it is a powernowd bug, but cpufreqd doesnt work for me. I have a HP8710p laptop, im not sure, but I think the processors are Intel

To see what processors you have, post the output of:
```
$cat /proc/cpuinfo
```

---

### Post by andreselsuave on 2009-06-03
```
processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
stepping	: 11
cpu MHz		: 2201.000
cache size	: 4096 KB

```

I switched from powernowd to cpufreqd and now Im stuck in 2.2 GHz with the AC cord and 1.6 GHz with batteries, with no control at all over the frequency (can't change it with cpu scaling applet or sudo cpufreqd-set). I will try later editing the /etc/cpufreqd.conf and I will post the results

---

### Post by Pépou on 2009-06-06
Having this exact same issue on a dual core (inspiron 6400). This problem is very annoying, my computer is so slow.

$ cat /proc/cpuinfo

> processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping	: 8
cpu MHz		: 1833.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm
bogomips	: 3656.95
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr pdcm
bogomips	: 3657.72
clflush size	: 64
power management:

$ cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq

> 1833000

---

### Post by Aped on 2009-06-06
Given the relatively low volume of feedback from gurus/devs here, I'm going to try a kernel recompile specifying the proper cpu; being a noob this will possibly constitute quite an undertaking, but if it works I'll let you guys know.



[edit]
So while looking into this I decided (reasonably) to get my cpu info to make sure I was setting CFlags properly for the compile; I checked my /proc/cpuinfo and lo and behold it has my CPU listed properly at 1.6GHz, up from the 600MHz previously listed. 1.6GHz is the proper number. 

I haven't changed anything, haven't rebooted, the only thing I can recall having done that might have changed it was a frustrated sudo killall cpufreqd - check and see if that does anything for you guys? I'm not exactly complaining but id love to know what happened to change this. 

```

andrew@andrew-laptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.60GHz
stepping	: 8
cpu MHz		: 1600.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips	: 3191.71
clflush size	: 64
power management:

```

---

### Post by andreselsuave on 2009-06-06
For Pepou, I would say, try in other forum threads, I've seen some workarounds disabling ACPI and some possible solutions for you loading some acpi kernel modules u might be missing. 

For the rest of you in the thread, I want to post my experience with cpufreqd, as opposite to powernowd. 

As I said in a previous post, my processor is a dual-core intel. Powernowd has been buggy for a while for me, getting stuck at lowest frequency sometimes. 

Switching to cpufreqd has been very positive. The cpu management is more flexible and intelligent (in my opinion). The only drawback is you cannot force the cpu into a frequency using the applet. At least I can't by now, but I will try soon. And the config file is easy to edit to suit your needs. And the best part... not buggy at all!!

Very recommended. Maybe it's because powernowd is apparently more oriented to AMD processors. You should give cpufreqd a try.

PS: I will post when I find out how to change the frequency on-the-fly with cpufreqd.

---

### Post by Pépou on 2009-06-07
OK that's the beginning of a solution ! Now my cpu is stuck at 1,83 Ghz (the maximum frequency).

---

### Post by andreselsuave on 2009-06-07
>  OK that's the beginning of a solution ! Now my cpu is stuck at 1,83 Ghz (the maximum frequency).
Did u get cpufreqd or did you disable acpi? If you have disabled acpi you have no control over your cpu.

---

### Post by Pépou on 2009-06-07
I installed cpufreqd and remove powernowd.
The CPU is scaling between 1,33Ghz and 1,83Ghz.

Most of the time it is stuck at 1,33Ghz..

Finally, the problem isn't that solved..

That's a very big problem for me, that appeared on Jaunty and which wasn't on precedent versions of ubuntu.

---

### Post by kedmond on 2009-06-11
My CPU scaling is all F'ed up.  I have a Centrino 2 processor, AKA the T9500 Core 2 Duo.  I'm running Ubuntu 9.04.  I'm using ACPI with CPUFREQD.  Basically, I'm stuck in "performance" mode at all times, running at 2.54 GHz.  Then, when I run something processor intensive, it drops to 1.6 GHz.  It used to fall to 800 MHz.  Not sure what changed.  Anyways, it shoots back up to 2.54 GHz after the processing is complete.  It makes me SO mad when I'm trying to meet a deadline, and my computer decides to be slow only when I need it.

Anyways, I ran "sudo killall cpufreqd" and it's maxed out at all times.  No more BS.  I can't believe no dev's have posted a fix to this yet.  It's a very troubling problem.

Thanks.

-Kazem

---

### Post by xylaq on 2009-06-19
My issue was that scaling would work for a short while but then get stuck at 800MHz.  I found entroes like this in daemon.log

cpufreqd: open_acpi_event : Couldn't connect to acpid socket /var/run/acpid.socket (No such file or directory)

The socket file /var/run/acpid.socket is created by the acpid daemon (see /etc/default/acpid)

Not really knowing why and quite desperate to find a solution, I changed the start sequence of acpid with the following


```

sudo update-rc.d -f acpid remove
sudo update-rc.d acpid start 99 2 3 4 5 . stop 99 0 1 6 .

```

I've been running like this for a couple of days now and scaling is working fine for me and nothing else appears to be broken.  Don't ask me why this works but it does.  I'm still experiencing frequent freeze problems but that's another story.

---

### Post by nocnokneo on 2010-08-26
Has anyone had success finding a real solution to this problem? I'm having the same issue on a Intel Core2 Duo system (Dell XPS m1330) running Ubuntu 10.04 (lucid). Disabling ondemand (`sudo update-rc.d ondemand disable`) seemed to help a little, but occasionally the CPU drops to 800 MHz and gets stuck stuck there until I reboot.

---

### Post by neoflight on 2010-12-19
Has anyone solved this problem. Instead of min, my system is stuck at max. 
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
ondemand
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq 
**2400000**
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver 
acpi-cpufreq

```

```
cat /proc/cpuinfo ==>
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
**cpu MHz		: 2400.000**
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts tpr_shadow vnmi flexpriority
bogomips	: 4799.76
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by conorsulli on 2010-12-27
Maverick 10.10 stuck at 1.ghz on ac power and stuck on ondemand on battery
one time i pulled the ac out with no battery and it got stuck at 2ghz for a while but the fan was going wild

conor@conor-Studio-1735:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 3990.43
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips	: 3990.92
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

---

