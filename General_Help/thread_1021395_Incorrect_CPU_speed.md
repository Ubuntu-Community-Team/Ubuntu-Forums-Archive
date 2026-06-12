---
title: "Incorrect CPU speed?"
date: 2008-12-25
forum: General Help
---

### Post by Beautysdeath on 2008-12-25
I just noticed last night my cpu speed is not correct. In the past it has always run at 2200mhz.
this is the info from Cat /pro/cpuinfo

root@LordLazra:~# cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 47
model name	: AMD Athlon(tm) 64 Processor 3400+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good nopl pni lahf_lm
bogomips	: 2004.15
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

The system is a compaq presario sr1820nx
I am running 2.5gigs ram
A8N-la mobo
This is a HP board however the board was assembled in china so it is not nessacry to us HPs site for bios and driver updates just so you know :)

Any help to fix this would be great I have noticed a serious drop in performance.

---

### Post by glotz on 2008-12-25
For what it's worth, you can select the clock speed in some BIOS setups.

---

### Post by kerry_s on 2008-12-25
it looks like it's just throttled down. right click your panel and add the cpu control applet, i have no idea what its called, you'll just have to look.

---

### Post by Beautysdeath on 2008-12-25
> **kerry_s said:**
> it looks like it's just throttled down. right click your panel and add the cpu control applet, i have no idea what its called, you'll just have to look.

Powernowd allowed me to change the cpu settings thanks for the point in the right place.

---

### Post by ingeniera on 2011-01-15
Hello I installed powernowd i have no idea how to configure it though and I cannot find it in the panel or else where..

---

### Post by cchhrriiss121212 on 2011-01-15
You do not need powernowd. Right click on the top panel, Click "Add to panel". Then select "CPU Frequency Scaling Monitor" and click add.

---

### Post by ingeniera on 2011-01-15
I can't find this tool in the panel...only two tools that allow cpu monitoring in the form of small graphs! I have version 4.6.2 (Xfce 4.6)

---

### Post by cchhrriiss121212 on 2011-01-15
Sorry I missed that this is on XFCE. AFAIK there is no native scaling applet for this environment, but you can use xfapplet which lets you use gnome applets in XFCE.

---

### Post by ingeniera on 2011-01-15
Thanks, I got the tool but it does not change the mode to conservative or powersave. I checked help and it says:

Unfortunately, CPU frequency scaling can currently only be monitored on
     Linux machine that have support in the kernel. It can however, support the
     several generations of frequency scaling interfaces in the kernel.
    
So, how do I know if I have this support in the kernel?
I don't mind putting another version of Gnome if it is light as Xubuntu. With Ubuntu I had no problem but was heavy.

---

### Post by cchhrriiss121212 on 2011-01-15
The generic kernel should have this feature, but some CPUs don't support scaling, what model do you have?

---

### Post by rnerwein on 2011-01-15
> **ingeniera said:**
> Thanks, I got the tool but it does not change the mode to conservative or powersave. I checked help and it says:

Unfortunately, CPU frequency scaling can currently only be monitored on
     Linux machine that have support in the kernel. It can however, support the
     several generations of frequency scaling interfaces in the kernel.
    
So, how do I know if I have this support in the kernel?
I don't mind putting another version of Gnome if it is light as Xubuntu. With Ubuntu I had no problem but was heavy.

hi
i guess the cpu frequncy on your system is driven by the load you have on it . it's not Windows.
if you are able to open a shell terminal  than thry ( on a single core one,  on a dual core two ... and so on )
in a terminal.
in each terminal type:

while:
do
:
done

this will cause the system to turn in a never ending loop for each shell.
then after two or 3 seconds you will see your true cpu speed.
[COLOR=Red]to stop this loops you have to type "ctr c" in each terminal window[/COLOR].
--> hint: never try this test in a realtime shell !!!!!

cioa

---

### Post by ingeniera on 2011-01-15
It actually worked after a restart. Thank you for your help! :))

---

