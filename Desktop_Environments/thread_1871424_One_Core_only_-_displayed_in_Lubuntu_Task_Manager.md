---
title: "One Core only - displayed in Lubuntu Task Manager"
date: 2011-10-28
forum: Desktop Environments
---

### Post by Orographic on 2011-10-28
Hi all,

Really enjoying the 11.10 version of Lubuntu. Only prob I am having thus far is that only one core shows up in the Task Manager. In Ubuntu and Mint, its always been four cores for my Core i3, even though technically it has two cores.

Any thoughts on what to do? Does only the 64bit edition of Lubuntu support more cores?

I am using 32bit edition of Lubuntu 11.10.

My system is GAH55-USB3 motherboard, 4GB of RAM, with onboard HD graphics.

Curiously, when I enter this into terminal, I get two cores listed:

sudo cat /proc/cpuinfo 

Terminal readout:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping	: 2
cpu MHz		: 1197.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
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
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6133.07
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping	: 2
cpu MHz		: 3059.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 4
initial apicid	: 4
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6133.13
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping	: 2
cpu MHz		: 3059.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6133.12
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping	: 2
cpu MHz		: 1197.000
cache size	: 4096 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 2
apicid		: 5
initial apicid	: 5
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 6133.12
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual

---

### Post by 3Miro on 2011-10-28
/proc/cpuinfo is what Ubuntu sees and uses. You have 4 cores numbered 0, 1, 2 and 3. i3 has two cores with Intel Ht, which means it shows up as 4 cores.

Which task manager are you looking at and how do you see only 1 core?

---

### Post by Orographic on 2011-10-28
Thanks 3Miro, I appreciate your response.

In Lubuntu, the default Task Manager is LXTask 0.1.4. It just has two usage bars at the top, one on the left shows CPU usage in percentage terms and the right bar shows memory usage. 

Here is an image of the Task Manager:


[https://picasaweb.google.com/lh/photo/BdaW7EhxtRoaG_a62X9XXseSFEbI8NoLw2wb6hf38Cw?feat=directlink](https://picasaweb.google.com/lh/photo/BdaW7EhxtRoaG_a62X9XXseSFEbI8NoLw2wb6hf38Cw?feat=directlink)

So, what task manager could I install instead of the default one? I've made an image of Lubuntu with Clonezilla, so can easily restore it if something goes awry.

I really like Lubuntu, reminds me a lot of Ubuntu a couple of years ago. Simple, clean inferface, that is quite easy to customise.

---

### Post by amjjawad on 2011-10-29
I replied you on my thread :)

---

### Post by 3Miro on 2011-10-29
> **Orographic said:**
> Thanks 3Miro, I appreciate your response.

In Lubuntu, the default Task Manager is LXTask 0.1.4. It just has two usage bars at the top, one on the left shows CPU usage in percentage terms and the right bar shows memory usage. 

Here is an image of the Task Manager:


[https://picasaweb.google.com/lh/photo/BdaW7EhxtRoaG_a62X9XXseSFEbI8NoLw2wb6hf38Cw?feat=directlink](https://picasaweb.google.com/lh/photo/BdaW7EhxtRoaG_a62X9XXseSFEbI8NoLw2wb6hf38Cw?feat=directlink)

So, what task manager could I install instead of the default one? I've made an image of Lubuntu with Clonezilla, so can easily restore it if something goes awry.

I really like Lubuntu, reminds me a lot of Ubuntu a couple of years ago. Simple, clean inferface, that is quite easy to customise.

LXTask doesn't show individual core load. I only know of Gnome-System-Monitor that does that (you have in the Software Center). The 100% of LXTaks are the total for all cores, if you see 25% then you are using 1/4 cores, if you see 50% you are using 2/4 cores, 75% is for 3/4 cores.

---

### Post by Orographic on 2011-10-31
Thanks guys, makes sense now. :)

---

### Post by amjjawad on 2011-10-31
> **Orographic said:**
> Thanks guys, makes sense now. :)

:)

---

