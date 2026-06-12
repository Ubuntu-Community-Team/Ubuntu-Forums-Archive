---
title: "cpu not being maximized"
date: 2007-12-01
forum: Desktop Environments
---

### Post by thekid on 2007-12-01
hello there,

I disabled CPU scaling for my ubuntu 7.0 64 bit because every time it scales up/down my cpu, my screen freezes. But now I realize that ubuntu is only using 50% of my cpu.. It caps my CPU at 1 GHZ.. But I actually have a 2.2 GHZ CPU. Please show me how to fix this. (I don't want to turn on cpu scalling because It freezes my cpu. In fact, I removed those packages). Some info that may be helpful to you guys. Thanks in advance. 

cat /proc/cpuinfo

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 12
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 0
cpu MHz         : 1000.061
cache size      : 512 KB
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up lahf_lm
bogomips        : 2002.26
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

### Post by didier on 2007-12-02
for instant results do the following
sudo cpufreq-selector -g performance

to keep changes after a reboot for a laptop
vi ~/.gconf/apps/gnome-power-manager/cpufreq/%gconf.xml
change the stringvalue from ondemand to performance

<?xml version="1.0"?>
<gconf>
<entry name="policy_battery" mtime="1196433352" type="string">
<stringvalue>performance</stringvalue>
</entry>
<entry name="policy_ac" mtime="1196433352" type="string">
<stringvalue>performance</stringvalue>
</entry>
</gconf>

and for a desktop its the same procedure but the location has changed
~/.gconf/apps/gnome-power-manager/%gconf.xml

---

### Post by thekid on 2007-12-02
thank you :D

---

