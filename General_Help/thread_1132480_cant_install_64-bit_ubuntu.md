---
title: "cant install 64-bit ubuntu"
date: 2009-04-21
forum: General Help
---

### Post by frank fertur on 2009-04-21
can't install 64-bit ubuntu on because kernel only detects an i686 cpu. My computer has amd 64, but I already installed 32-bit ubuntu. I think that I need to reformat my computer. I am new to ubuntu. Can somebody please help me

---

### Post by pytheas22 on 2009-04-21
What is the output (from your current Ubuntu installation) of this command:
```

cat /proc/cpuinfo
```

And what kind of processor do you have (please give as many specific details as possible)?

---

### Post by frank fertur on 2009-04-22
here is my information thanks for your help I'd rather get this going than have to go back to windows
i-laptop:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 44
model name	: Mobile AMD Sempron(tm) Processor 3000+
stepping	: 2
cpu MHz		: 800.000
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up pni lahf_lm
bogomips	: 1591.80
clflush size	: 64
power management: ts fid vid ttp tm stc

---

### Post by FredB on 2009-04-22
Looks like your CPU is a 32 bits one.

Here is the cat /proc/cpuinfo of my AMD64 cpu (dual core, showing the first one only) :

```
fred@fredo-ubuntu:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 104
model name    : AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
stepping    : 1
cpu MHz        : 800.000
cache size    : 256 KB
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
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips    : 1600.46
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps
```

If you don't have svm flag, you don't have amd virtualization technology.

---

### Post by pytheas22 on 2009-04-22
Yes, it doesn't look like your processor is 64-bit (unless Linux is detecting it incorrectly, but I've never seen that before with a CPU).  However, that doesn't mean you can't use Ubuntu--Ubuntu will work absolutely fine on a 32-bit processor as long as you install the 32-bit version.  Is there a reason why you thought you needed 64-bit?

---

