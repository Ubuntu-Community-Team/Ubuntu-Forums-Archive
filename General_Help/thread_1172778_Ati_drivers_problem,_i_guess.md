---
title: "Ati drivers problem, i guess : /"
date: 2009-05-28
forum: General Help
---

### Post by Ubmega on 2009-05-28
Hi everyone, i'm new to ubuntu, left xp 2 days ago.
I like this OS a lot and i would like to keep using it but i have a problem that i can't find the solution for.
The problem is the "general slowness" of ubuntu, it all feels really slow, even the most simple tasks like opening a window or resizing it requires 5 seconds to complete, i think this isn't normal, mostly because my pc should be able to run ubuntu at full speed i think, quad core/4gb ram/ati 3600 hd videocard (i know the card isn't really the best but it should do the job, right?).
I think it's a drivers problem, firstly used the drivers that ubuntu suggested me, then, since i wanted to fix this problem i downloaded the offical ati drivers and installed them (following a guide since i'm a total newbie) and that didn't work.
Another thing is that whenever i move windows or resize etc my cpu usage goes up to 100%.
If this was a driver problem anyway i wouldn't even know how to reinstall them.

Please help me, i don't want to go back to xp...

I'm in your hands. :|

note1 : I use Ubuntu 9.04

note 2: This is what top command gives me:

top - 04:48:23 up 42 min,  2 users,  load average: 0.19, 0.18, 0.14
Tasks: 169 total,   2 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.3%sy,  0.0%ni, 97.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3355544k total,   725836k used,  2629708k free,    47516k buffers
Swap:  9823708k total,        0k used,  9823708k free,   355884k cached

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3990 omega     20   0  177m  66m  21m S    5  2.0   1:45.92 firefox            
 5864 omega     20   0 33536  13m 9596 S    2  0.4   0:00.85 gnome-terminal     
 3077 root      20   0  395m  68m  21m S    2  2.1   2:37.12 Xorg               
    1 root      20   0  1908  784  564 S    0  0.0   0:01.28 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.12 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.08 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/3        
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3  

By the way, that's an idle view, normally when i do something the Xorg process drains all the cpu...

Sorry for my bad english.

---

### Post by lavinog on 2009-05-29
The default driver is the open sourced radeon driver. The version included in jaunty is outdated and doesn't include much support for the 3000+ cards. You can go to system>administration>hardware drivers and install the proprietary ati driver. It works much better than the open source driver. One other thing is that the proprietary driver is 2.5 versions old and doesn't have the latest enhancements for desktop effects, but it should improve your current situation.

I have a hd3650 with the latest ati proprietary driver (fglrx 9-5), and so far so good with it. A new driver is released each month. There are occasions that a newer driver is worse than the previous. 9-3.5 is what comes with ubuntu. 9-3 is not compatible with the new xorg. 9-4 is not compatible with older (> 3yrs) cards, it fixed some major issues with desktop effects, but introduced a lot of screen corruption. 9-5 seems to fix the corruption issue.

---

### Post by vivedekananda on 2009-05-29
Seems like your driver isn't installed properly. Could you please post your /etc/X11/xorg.conf file here as well as the output from "fglrxinfo".
Also try running "glxinfo | grep direct" in a terminal, you should get
"direct rendering: Yes".

---

### Post by Yellow Pasque on 2009-05-29
> install the proprietary ati driver. It works much better than the open source driver.
The proprietary driver is actually slower with 2D acceleration (it uses XAA while the open-source drivers use EXA). Of course, the open-source drivers don't have any 3D hardware accleration for RadeonHD yet, so..

---

### Post by lavinog on 2009-05-29
> **Temüjin said:**
>  the open-source drivers don't have any 3D hardware accleration for RadeonHD yet, so..
Apparently 3d support was added to the latest version, but I haven't tried them yet.

---

