---
title: "Youdao dictionary &quot;Mandarin user needed here&quot;!"
date: 2020-04-25
forum: Desktop Environments
---

### Post by makem2 on 2020-04-25
```

makem@ssdTOSH:~$ lscpu
Architecture:        x86_64
CPU op-mode(s):      32-bit, 64-bit
Byte Order:          Little Endian
CPU(s):              4
On-line CPU(s) list: 0-3
Thread(s) per core:  2
Core(s) per socket:  2
Socket(s):           1
NUMA node(s):        1
Vendor ID:           GenuineIntel
CPU family:          6
Model:               61
Model name:          Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz
Stepping:            4
CPU MHz:             2988.840
CPU max MHz:         3000.0000
CPU min MHz:         500.0000
BogoMIPS:            4788.66
Virtualisation:      VT-x
L1d cache:           32K
L1i cache:           32K
L2 cache:            256K
L3 cache:            4096K
NUMA node0 CPU(s):   0-3
Flags:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36  clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb  rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology  nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est  tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe  popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm  3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp  tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep  bmi2 erms invpcid rdseed adx smap intel_pt xsaveopt dtherm ida arat pln  pts md_clear flush_l1d
makem@ssdTOSH:~$

```

```

makem@ssdTOSH:~$ uname -a
Linux ssdTOSH 4.15.0-96-generic #97-Ubuntu SMP Wed Apr 1 03:25:46 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
makem@ssdTOSH:~$

```
```

makem@ssdTOSH:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic
makem@ssdTOSH:~$

```

I have Installed the latest .deb of Youdao dictionary and it does work but not satisfactorily.

It is very slow to show the pop-up translation every time the mouse is hovered over a word or a word is highlighted.

After several translations the machine fan comes on and I find the processor is maxed out, The only way to stop this is by rebooting. Even exiting the program has no effect.

Youdao uses /tmp and when first started the only use there is:

```

-rw-rw-rw-  1 makem makem      5 Apr 25 17:18 sogou-qimpanel:0.pid
srwxrwxr-x  1 makem makem      0 Apr 25 17:18 sogou-qimpanel-cellmakem
srwxrwxr-x  1 makem makem      0 Apr 25 17:18 sogou-qimpanelmakem

```

When it gets 'excited' the use is (snip from all the entries):

```

drwx------  2 makem makem   4096 Apr 25 17:00 Temp-0221f889-b496-4821-a2a2-00cd679e73f3
drwx------  2 makem makem   4096 Apr 25 17:02 Temp-587f34ba-8a6a-4ebe-94d5-c6c7cc5abed7
drwx------  2 makem makem   4096 Apr 25 17:00 Temp-6d00d0ef-f277-4eb2-8674-3f68f9f6351c
-rw-------  1 makem makem 720054 Apr 25 17:15 tess_22caf399.bmp
-rw-r--r--  1 makem makem      0 Apr 25 17:15 tess_77k4hcwg.hocr
-rw-r--r--  1 makem makem      0 Apr 25 17:15 tess_7oeshim5.hocr
-rw-------  1 makem makem 720054 Apr 25 17:15 tess_8zojufi3.bmp
-rw-------  1 makem makem 720054 Apr 25 17:15 tess_bjqr2rxk.bmp
-rw-------  1 makem makem 662454 Apr 25 17:16 tess_d32unpib.bmp
-rw-r--r--  1 makem makem      0 Apr 25 17:15 tess_dg03w0_o.hocr
-rw-r--r--  1 makem makem      0 Apr 25 17:15 tess_ep6e8ops.hocr
-rw-r--r--  1 makem makem      0 Apr 25 17:16 tess_h24ad5tt.hocr
-rw-r--r--  1 makem makem      0 Apr 25 17:15 tess_i0d82_vy.hocr
-rw-------  1 makem makem 606454 Apr 25 17:15 tess_i5o2jid2.bmp
-rw-------  1 makem makem 720054 Apr 25 17:15 tess_lonbi65q.bmp
-rw-------  1 makem makem 368854 Apr 25 17:15 tess_mtq4bbo5.bmp
-rw-------  1 makem makem 720054 Apr 25 17:15 tess_ou1vp52r.bmp
-rw-r--r--  1 makem makem      0 Apr 25 17:15 tess_pleyi2p4.hocr
-rw-r--r--  1 makem makem      0 Apr 25 17:15 tess_sa4v5kk8.hocr
-rw-------  1 makem makem 720054 Apr 25 17:15 tess__v07oo95.bmp
-rw-r--r--  1 makem makem      0 Apr 25 17:15 tess_x8x3i8ih.hocr

```

At the same time there are multiple entries in task manager such as:

```

tesseract/tmp/tess_5j6j7z_6-l end hocr

```
I have no idea what is going on there and it does not cease when the program is exited. It seems as if each entry is doing it's own thing, regardless.

I am unable to read Mandarin so am unable to correctly setup the program and wonder if that is why I get this problem.

Is there any Chinese linux user who could either guide me through setup, or, point me to an English guide?

---

### Post by Holger_Gehrke on 2020-04-26
Something is using tesseract (an OCR program that will produce html with a fixed structure called hocr) to read bitmap-files ... No idea why a dictionary would do that.

Holger

---

### Post by makem2 on 2020-04-26
I noticed that the bmp files were areas where the mouse had stopped. It appeared that the program was permanently scanning where the mouse pointer was located and if it halted then the dictionary used what it had scanned in that area to produce  the popup 'menu' with choices.

I suppose if the mouse moved on before the program had decided to produce a popup or did not have time to produce a popup, it started again and again and again!

I saw that if I made positive movement stops of the curser the program was stable and produced the correct popup once. That made me wonder if the settings were wrong but I did hope the default settings would work.

The program works fine on Windows 10 but it seems is flaky in Ubuntu. Need a Chinese man (oops), person now their lockdown, except for Russia/China border, has ended.

I wonder if a mod would add,"Mandarin user needed here", to the thread title lol.

---

### Post by mörgæs on 2020-04-26
You can edit the thread title yourself. Just click 'advanced'.

---

