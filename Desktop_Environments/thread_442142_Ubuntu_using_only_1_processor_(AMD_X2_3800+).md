---
title: "Ubuntu using only 1 processor? (AMD X2 3800+)"
date: 2007-05-13
forum: Desktop Environments
---

### Post by chien on 2007-05-13
Hi,

I just replaced my old cpu with a AMD X2 3800+

problem is when I do a 'cat /proc/cpuinfo', it returns

carlos@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
stepping        : 2
cpu MHz         : 2305.704
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 4613.30
clflush size    : 64

carlos@ubuntu:~$ 



However, I've seen 'cat /proc/cpuinfo' returning  information of 2 cpus (see 'processor: 0' and 'processor: 1' below) for some people in the forum, for example this guy has:

justin@rain:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 67
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips	: 2011.05
clflush size	: 64

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 67
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips	: 2011.05
clflush size	: 64






does this mean that my ubuntu is using only 1 core??? plz someone advise me

---

### Post by Hobo Joe on 2007-05-13
I'm pretty sure it uses both, You should be fine.

---

### Post by tgm4883 on 2007-05-15
> **Hobo Joe said:**
> I'm pretty sure it uses both, You should be fine.

Nice, any way to back that up or should he just take your word for it?

chien, do this and post the output

```
uname -a
```

:EDIT:

My X2 3800+ lists both cores

---

### Post by zdude on 2007-05-15
If you are running the generic linux kernel you should be ok.  Running uname -a you should see something like this :Linux z-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
This is from a X2 3800 box running Feisty.

---

