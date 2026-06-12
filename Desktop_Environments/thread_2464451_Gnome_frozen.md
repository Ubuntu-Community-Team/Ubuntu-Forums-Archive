---
title: "Gnome frozen"
date: 2021-07-02
forum: Desktop Environments
---

### Post by daca4 on 2021-07-02
Hello all,

   I have an issue with gnome on ubuntu 21.04. After startup environment works well, but after some time whole gnome is frozen. I am able to move mouse, but nothing else. The all environment looks like opened picture where you can move mouse. 
   The kernel looks good, I am able to switch terminal ALT+F4 for example. To restart it I am going to terminal ALT+F3 for example login and kill all processes of that user. I tried use ALT+F2 and 'R' but it didn't work. 

   Could You give me some hints where I should start to find solution ? 

Thanks in advance,
Dawid

---

### Post by dddman on 2021-07-02
Hello

First tell us about your equipment.  How much ram do you have, what cpu and what video processor?  Is this a fresh install?

---

### Post by ActionParsnip on 2021-07-02
Is it a dual boot? Does the system have a make and model? Has the system always behaved like this or is it new behavior recently?

---

### Post by daca4 on 2021-07-02
CPU: 
```
 lscpuArchitecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   46 bits physical, 48 bits virtual
CPU(s):                          48
On-line CPU(s) list:             0-47
Thread(s) per core:              2
Core(s) per socket:              12
Socket(s):                       2
NUMA node(s):                    2
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           63
Model name:                      Intel(R) Xeon(R) CPU E5-2678 v3 @ 2.50GHz
Stepping:                        2
CPU MHz:                         1200.000
CPU max MHz:                     3300,0000
CPU min MHz:                     1200,0000
BogoMIPS:                        4988.86
Virtualization:                  VT-x
L1d cache:                       768 KiB
L1i cache:                       768 KiB
L2 cache:                        6 MiB
L3 cache:                        60 MiB
NUMA node0 CPU(s):               0-11,24-35
NUMA node1 CPU(s):               12-23,36-47
Vulnerability Itlb multihit:     KVM: Mitigation: Split huge pages
Vulnerability L1tf:              Mitigation; PTE Inversion; VMX conditional cac
                                 he flushes, SMT vulnerable
Vulnerability Mds:               Mitigation; Clear CPU buffers; SMT vulnerable
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled 
                                 via prctl and seccomp
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __use
                                 r pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, IBPB condi
                                 tional, IBRS_FW, STIBP conditional, RSB fillin
                                 g
Vulnerability Srbds:             Not affected
Vulnerability Tsx async abort:   Not affected
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mt
                                 rr pge mca cmov pat pse36 clflush dts acpi mmx
                                  fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb
                                  rdtscp lm constant_tsc arch_perfmon pebs bts 
                                 rep_good nopl xtopology nonstop_tsc cpuid aper
                                 fmperf pni pclmulqdq dtes64 monitor ds_cpl vmx
                                  smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pci
                                 d dca sse4_1 sse4_2 x2apic movbe popcnt tsc_de
                                 adline_timer aes xsave avx f16c rdrand lahf_lm
                                  abm cpuid_fault epb invpcid_single pti intel_
                                 ppin ssbd ibrs ibpb stibp tpr_shadow vnmi flex
                                 priority ept vpid ept_ad fsgsbase tsc_adjust b
                                 mi1 avx2 smep bmi2 erms invpcid cqm xsaveopt c
                                 qm_llc cqm_occup_llc dtherm ida arat pln pts m
                                 d_clear flush_l1d



```

RAM:
```
free -mh              total        used        free      shared  buff/cache   available
Mem:          125Gi        18Gi        93Gi       1,2Gi        14Gi       105Gi
Swap:            0B          0B          0B



```

GPU:
```
nvidia-smi Fri Jul  2 17:00:24 2021       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 460.80       Driver Version: 460.80       CUDA Version: 11.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  Quadro M4000        Off  | 00000000:81:00.0  On |                  N/A |
| 56%   67C    P0    58W / 120W |   2121MiB /  8124MiB |     19%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      3161      G   /usr/lib/xorg/Xorg               1459MiB |
|    0   N/A  N/A      3303      G   /usr/bin/gnome-shell              203MiB |
|    0   N/A  N/A      3786      G   ...AAAAAAAAA= --shared-files      309MiB |
|    0   N/A  N/A      4061      G   ...AAAAAAAAA= --shared-files       18MiB |
|    0   N/A  N/A      6502      G   ...og-level=0 --shared-files       65MiB |
|    0   N/A  N/A     17518      G   ...AAAAAAAAA= --shared-files       51MiB |
+-----------------------------------------------------------------------------+
```

This is not fresh install. It was working more than 6 months. I think it was because of I install teams (it was only one change due to working environment, Now I uninstalled it and looks better, hope it will work.

---

### Post by dddman on 2021-07-02
Sorry
I should of asked for the output of
```
inxi -b
```
Any clues here
```
dmesg
```
Also check the system/kernel log

---

### Post by daca4 on 2021-07-02
Here is the result of command:
```
inxi -bSystem:
  Host: viper Kernel: 5.11.0-22-generic x86_64 bits: 64 
  Desktop: GNOME 3.38.4 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop Mobo: HUANANZHI model: X99-T8D v: V1.0 
  serial: <superuser required> UEFI: American Megatrends v: 5.11 
  date: 04/02/2020 
CPU:
  Info: 2x 12-Core Intel Xeon E5-2678 v3 [MT MCP SMP] speed: 1198 MHz 
  min/max: 1200/3300 MHz 
Graphics:
  Device-1: NVIDIA GM204GL [Quadro M4000] driver: nvidia v: 460.80 
  Display: x11 server: X.Org 1.20.11 driver: loaded: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1: 3840x2160~60Hz 
  2: 3840x2160~60Hz 3: 3840x2160~60Hz 4: 3840x2160~60Hz 
  OpenGL: renderer: Quadro M4000/PCIe/SSE2 v: 4.6.0 NVIDIA 460.80 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
Drives:
  Local Storage: total: raw: 5.1 TiB usable: 5.1 TiB used: 150.59 GiB (2.9%) 
Info:
  Processes: 674 Uptime: 7m Memory: 125.77 GiB used: 3.74 GiB (3.0%) 
  Shell: Bash inxi: 3.3.01 



```

I found the issue - Nautilus. When I am click "Other Locations" gnome is frozen. I tried uninstall Nautilus remove "~/.config/Nautilus" and install again, but still same and config is keept somewhere as You can see on image. There is still 'bookmark' 'KVM' which shouldn't be visible after that purge of app.



Funny is that am able to use 'other location' in other apps like chrome to find the image ...

---

### Post by zebra2 on 2021-07-03
So Gnome freezes. If you do a {CTRL}{ALT}{DELETE} do you get a pop-up Cancel : Logout? If yes then if you {right arrow} and choose Log-out does the system log-out and clear the freeze? I'm interested in knowing the results of this if you don't mind.

---

