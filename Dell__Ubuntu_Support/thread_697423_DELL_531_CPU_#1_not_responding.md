---
title: "DELL 531: CPU #1 not responding"
date: 2008-02-15
forum: Dell  Ubuntu Support
---

### Post by PaJoe on 2008-02-15
I need some help, thanks in advance


I lost my dual core capability, I tried resetting the defaults in the BIOS, I tried booting from a live cd  neither worked. I am using the 32 bit version of Ubuntu. 
(ON EDIT: The 64 bit version of Kubuntu live desktop seems to work.) 

Previously, I thought the  the second core was working OK with the 32 bit version as well. It's a Dell 531s refurb, originally pre-loaded with Vista - I had it for about 2 months and it was working fine with Ubuntu/Kubuntu 

My biggest concern is the message:

[    5.352000] CPU #1 not responding - cannot use it.





Kernel (uname -r):   	 2.6.22-14-generic
Distribution: 	Ubuntu/Kubuntu 7.10 Gutsy



output from grep core/proc/cpuinfo:

$ grep core /proc/cpuinfo
core id         : 0
cpu cores       : 1


***********


and  ~$ cat /proc/cpuinfo:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps
bogomips        : 2011.07
clflush size    : 64

*****************************************
dmesg |grep CPU :


$ dmesg | grep CPU
[    0.000000] Initializing CPU#0
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f
[    0.376000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
[    5.352000] CPU #1 not responding - cannot use it.
[    5.392000] Brought up 1 CPUs
[    5.596000] Switched to high resolution mode on CPU 0

*****




************************************** Update **********************************




ON EDIT:

I tried the 64 bit version of Kubunut live desktop and it worked OK, not a hardware problem.

ubuntu@ubuntu:~$ uname -r
2.6.22-14-generic
ubuntu@ubuntu:~$ dmesg | grep CPU
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Initializing CPU#0
[   56.940673] CPU 0: aperture @ 44000000 size 32 MB
[   57.006626] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   57.087111] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   57.087113] CPU: L2 Cache: 512K (64 bytes/line)
[   57.087116] CPU 0/0 -> Node 0
[   57.087118] CPU: Physical Processor ID: 0
[   57.087119] CPU: Processor Core ID: 0
[   71.777594] Initializing CPU#1
[   71.855291] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   71.855294] CPU: L2 Cache: 512K (64 bytes/line)
[   71.855296] CPU 1/1 -> Node 0
[   71.855298] CPU: Physical Processor ID: 0
[   71.855299] CPU: Processor Core ID: 1
[   71.859208] Brought up 2 CPUs
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ grep core /proc/cpuinfo
core id         : 0
cpu cores       : 2
core id         : 1
cpu cores       : 2
ubuntu@ubuntu:~$


ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy misalignsse
bogomips        : 2011.04
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
stepping        : 1
cpu MHz         : 1000.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy misalignsse
bogomips        : 2011.04
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

---

### Post by PaJoe on 2008-02-16
It wasn't quick and  easy, but I recompiled the kernel to 2.6.24.2 using  KernelCheck [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)  which worked but I needed to do it several times until I learned you had to go into go into the configuration for Sound Advanced Linus System under PCI devices and select the HD Sound for the iIntel - even though I am not using the intel, in order to  get the sound working. 

In the process II also selected the "K7"  option as I am using an AMD 64 dual core.  I also needed to select memory higher than 4 gig so my full 4 gig of memory would be recognized. The first time I thought selecting 4 gig would do it, but had to go with the 64 gig - took several tries to get it all working.

The last  compille i used the directions at [http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel)
because I didn't need to download the source again and I didn't know how to set up kernelcheck to set up and compile without doiwnloading everything. It took a long time, several hours to recompile the kernel several times, I almost gave up and was ready to install the 64 bit version.

I needed to run envy again to reinstall my video drivers and I had to reinstall VirtualBox but it now seems to be working. I hope this helps someone else.

---

