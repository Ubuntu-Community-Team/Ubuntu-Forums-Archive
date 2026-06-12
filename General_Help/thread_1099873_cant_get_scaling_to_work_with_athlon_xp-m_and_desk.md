---
title: "cant get scaling to work with athlon xp-m and desktop motherboard"
date: 2009-03-18
forum: General Help
---

### Post by tominto on 2009-03-18
Hi all, I'm a complete newb and just installed ubuntu intrepid this week.  So far so good, except I can't seem to set up cpu scaling.  I have athlon xp mobile 2500 barton, which I'm using in an ASUS a7v8x mx se board.  The board is very basic and offers no bios adjustments for multipliers or fsb, and only jumpers on the board for fsb.  The multiplier startup default is only 6, giving me a measly 995 mhz (It should run at 1.8 ghz at least).  In windows I was successfully able to adjust the multiplier up to 14 using an application called cpumsr.  I would really like to be able to do the same thing in ubuntu, but I can't find a way.  I have done lots of research and followed suggestions for installing powernowd :"Setting up powernowd (1.00-1ubuntu2) ...
 * Starting powernowd...                                                                                 * CPU frequency scaling not supported...  ", cpufreqd:"Setting up cpufreqd (2.3.3-1) ...
No cpufreq interface found, not starting cpufreqd." etc to no avail. I tried cpuspeedy which gave me this error: " cpuspeedy max
cpuspeedy: error: ERROR_NO_INTERFACE

If you are running a v2.5/2.6 kernel, please make sure that:
  - That you have the core cpufreq and cpufreq-userspace modules
    compiled or loaded into the kernel.
  - The you have sysfs mounted /sys
  - That you have the cpufreq driver for your cpu loaded.

I've tried adding the CPU Frequency Scaling Monitor as a panel, but get the message "Cpu scaling unsupported".

Here's some specs from my cpu:
 cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 6
model		: 10
model name	: Mobile AMD Athl
stepping	: 0
cpu MHz		: 995.955
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
bogomips	: 1991.91
clflush size	: 32
power management: ts fid vid

and here, I hope, is all the relevant info from dmesg 

[    0.000000] Detected 995.955 MHz processor.
[    0.004549] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004555] CPU: L2 Cache: 512K (64 bytes/line)
[    0.031265] ACPI: Core revision 20080609
[    0.034143] ACPI: Checking initramfs for custom DSDT
[    0.704917] ENABLING IO-APIC IRQs
[    0.708194] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.747893] CPU0: AMD Mobile AMD Athl stepping 00
[    0.748031] Brought up 1 CPUs
[    0.748031] Total of 1 processors activated (1991.91 BogoMIPS).
[    0.748031] CPU0 attaching NULL sched-domain.
[   37.222213] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   37.231040] powernow: Trying ACPI perflib
[   37.233049] powernow: ACPI perflib can not be used in this platform
[   37.233060] powernow: ACPI and legacy methods failed
[   37.233065] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html)
[   37.950055] ACPI: WMI: Mapper loaded
[   38.416700] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[ 3943.373532] cpufreqd[7457]: segfault at 1c ip b7d8b0b6 sp bfa27f38 error 4 in libsysfs.so.2.0.1[b7d86000+9000]
[ 4025.943770] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[ 4025.952734] powernow: Trying ACPI perflib
[ 4025.958855] powernow: ACPI perflib can not be used in this platform
[ 4025.958867] powernow: ACPI and legacy methods failed
[ 4025.958872] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html)
[ 4068.928500] powernow-k8: Processor cpuid 6a0 not supported
[ 4672.676311] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[ 4672.685300] powernow: Trying ACPI perflib
[ 4672.693597] powernow: ACPI perflib can not be used in this platform
[ 4672.693625] powernow: ACPI and legacy methods failed
[ 4672.693630] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html)
[ 4682.173590] powernow-k8: Processor cpuid 6a0 not supported
[11789.274540] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[11789.283382] powernow: Trying ACPI perflib
[11789.304045] powernow: ACPI perflib can not be used in this platform
[11789.304059] powernow: ACPI and legacy methods failed
[11789.304064] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html)
[17114.327439] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[17114.336335] powernow: Trying ACPI perflib
[17114.338629] powernow: ACPI perflib can not be used in this platform
[17114.338640] powernow: ACPI and legacy methods failed
[17114.338645] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html)
[17436.018128] cpufreqd[11701]: segfault at 1c ip b7e350b6 sp bfbd17a8 error 4 in libsysfs.so.2.0.1[b7e30000+9000]
[17644.174086] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[17644.183005] powernow: Trying ACPI perflib
[17644.185195] powernow: ACPI perflib can not be used in this platform
[17644.185207] powernow: ACPI and legacy methods failed
[17644.185212] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html)


Surely if I can adjust the multiplier in windows with cpumsr, there is a way with ubuntu?  Maybe I'm missing a few steps with cpufreqd or powernowd and I need a good tutorial? Any help would greatly be appreciated.  Thanks

Tom

---

### Post by tominto on 2009-03-19
I'm still looking for a solution to my problem.  Please.  Anyone?

I want to do some cpu intensive things, so I really need the cpu running at its proper speed.  I can think of an alternative to this which involves a 'pinmod' to the actual cpu to get the higher multiplier, but I'd rather do this through software.

---

### Post by tominto on 2009-03-21
I found this tutorial [http://changelog.complete.org/archives/572-saving-power-with-cpu-frequency-scaling/comment-page-1](http://changelog.complete.org/archives/572-saving-power-with-cpu-frequency-scaling/comment-page-1), but I can't load any of the drivers with modprobe etc.  Nothing works.

Some more info about my system:

lsmod | grep cpufreq
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 

Please someone help me out.

---

### Post by tominto on 2009-03-22
bump:confused:

---

### Post by tominto on 2009-03-25
bump](*,)

---

### Post by dcstar on 2009-03-25
> **tominto said:**
> 
.......
and here, I hope, is all the relevant info from dmesg 

.......
[17644.183005] powernow: Trying ACPI perflib
[17644.185195] powernow: ACPI perflib can not be used in this platform
[17644.185207] powernow: ACPI and legacy methods failed
[17644.185212] powernow: **See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html)**


Surely if I can adjust the multiplier in windows with cpumsr, there is a way with ubuntu?  Maybe I'm missing a few steps with cpufreqd or powernowd and I need a good tutorial? Any help would greatly be appreciated.  Thanks

Tom

And what does going to that provided link tell you?

---

### Post by tominto on 2009-03-28
OOps...didnt see the link.  Thanks for pointing it out dcstar.
The link takes me here [http://www.yggdrasl.demon.co.uk/code/](http://www.yggdrasl.demon.co.uk/code/) and I'm assuming I need this patch [http://www.yggdrasl.demon.co.uk/code/powernow-k7-msr-2.6.8.1.patch](http://www.yggdrasl.demon.co.uk/code/powernow-k7-msr-2.6.8.1.patch) but I'm not sure what to do next.  Do I just download the patch and use it to patch powernow-k7.ko.  How do I do this?  patch -p0 < powernow-k7-msr-2.6.8.1.patch....something like that??

Please help, thanks

---

### Post by tominto on 2009-03-29
Can someone please help!!  Do I need to recompile the kernel, or the powernow module, with the above patch, or what?  I need to know what to do and how to do it.  Thanks

---

### Post by dcstar on 2009-03-30
> **tominto said:**
> Can someone please help!!  Do I need to recompile the kernel, or the powernow module, with the above patch, or what?  I need to know what to do and how to do it.  Thanks

That page has patches for all kernels up to 2.6.24.x, you have to use the correct one.

There are kernel HOWTOs for you to search out, no one will tell you what to do in this thread because it is too complex.

---

### Post by bowsermix on 2010-05-09
did u get to work? its a shame dosen't?  :(....5 days of triying...:mad: XD

---

