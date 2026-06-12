---
title: "KVM Virtualization not working"
date: 2009-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by SATA on 2009-12-23
I've been unable to use qemu-kvm on my Dell Optiplex 755

dmesg output when kvm-intel module is attempted to be loaded:
```
ryan@kgb:~$ dmesg | grep kvm
[   21.426697] kvm: disabled by bios
```And this is what is spat out when i try to start module manually:
```
ryan@kgb:~$ sudo /etc/init.d/qemu-kvm start
 * Loading kvm module kvm_intel
FATAL: Error inserting kvm_intel (/lib/modules/2.6.31-16-generic-pae/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported
   ...fail!
```Processor Information:
```
ryan@kgb:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8300  @ 2.83GHz
stepping        : 6
cpu MHz         : 2000.000
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 5652.33
clflush size    : 64
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 23
model name      : Intel(R) Core(TM)2 Duo CPU     E8300  @ 2.83GHz
stepping        : 6
cpu MHz         : 2000.000
cache size      : 6144 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority
bogomips        : 5652.40
clflush size    : 64
power management:
```I have also tried the techniques here with no joy: [http://reidablog.blogspot.com/2008/06/with-correct-bios-settings-enabled-on.html](http://reidablog.blogspot.com/2008/06/with-correct-bios-settings-enabled-on.html)



Any ideas anyone?

---

