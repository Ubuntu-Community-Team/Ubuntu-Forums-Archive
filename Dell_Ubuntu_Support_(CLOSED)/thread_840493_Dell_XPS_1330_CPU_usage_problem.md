---
title: "Dell XPS 1330 CPU usage problem"
date: 2008-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by -mbs- on 2008-06-25
Hello.

I have a cpu consumption problem on my Dell laptop. I am running Ubuntu 8.04 Hardy Heron with installed Nvidia graphics card. My CPU consumption is always above 15 on the cpu 1 and over 50 on the cpu 2 - This is just normal idle. My fan will not stop to spin around.

Have tried it with powertop. Nothing helped.

Right now i'm trying with the new BIOS update, but the fan is still loud under a clean installation.

Is there a solution to this?

Ubuntu 32-bit Hardy Heron
3 gb ram
T7500 Core 2 Duo
250 GB disk
128 MB nVidia GeForce 8400M GS

---

### Post by -mbs- on 2008-06-25
Sorry for double post. Just forget the "top" and the CPU temp.

top - 20:09:42 up 10 min,  2 users,  load average: 0.69, 0.46, 0.27
Tasks: 118 total,   3 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.0%us,  1.1%sy,  0.0%ni, 83.9%id,  0.0%wa,  0.9%hi,  0.0%si,  0.0%st
Mem:   3114500k total,   638144k used,  2476356k free,    18792k buffers
Swap:  9116848k total,        0k used,  9116848k free,   379732k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                        
 6239 mbs       20   0 40256  19m  12m S   17  0.6   1:10.79 gnome-system-mo                                                                                
 5639 root      20   0  169m  18m 6844 S   10  0.6   1:09.07 Xorg                                                                                           
 6228 mbs       20   0  176m  85m  21m S    2  2.8   0:22.07 firefox                                                                                        
 5408 haldaemo  20   0  6320 4336 3560 S    1  0.1   0:00.98 hald                                                                                           
 6267 mbs       20   0 75152  20m  11m R    1  0.7   0:00.70 gnome-terminal                                                                                 
 8640 root      20   0  2308 1124  852 R    1  0.0   0:00.08 top                                                                                            
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.74 init         

 

 

 

 

And the temp. is 56 celcius. ON IDLE! with only firefox (3 tabs) running.

 

Just updated the BIOS

---

### Post by zekica on 2008-06-25
From this, it looks like gnome-system-monitor application is using a lot of processor time. Can you run 'top' without gnome-system-monitor opened? And see what is the processor usage then.

---

### Post by -mbs- on 2008-06-25
> **zekica said:**
> From this, it looks like gnome-system-monitor application is using a lot of processor time. Can you run 'top' without gnome-system-monitor opened? And see what is the processor usage then.

Yes. Of cause

top - 21:29:56 up 2 min,  2 users,  load average: 1.00, 0.67, 0.27
Tasks: 115 total,   1 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.4%us,  1.0%sy,  0.0%ni, 91.7%id,  0.0%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:   3114500k total,   553692k used,  2560808k free,    13996k buffers
Swap:  9116848k total,        0k used,  9116848k free,   322064k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6300 mbs       20   0  257m  86m  24m S    9  2.8   0:05.47 firefox            
 5731 root      20   0  165m  14m 6260 S    3  0.5   0:06.02 Xorg               
 6274 mbs       20   0 66012  19m  10m S    1  0.6   0:00.50 gnome-terminal     
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.22 init     

But now the fan will not stop.

The temp is on 49 C now. 

I've installed powernowd and some other stuff to keep the temp down. I think the temp is looking fine. But the FAN!!! :(

---

### Post by -mbs- on 2008-06-25
The best temp i get is 44 on idle. Thats okay on a laptop.

So my next problem. The fan :)

---

### Post by sdennie on 2008-06-25
As stated above, gnome-system-monitor itself uses abnormally high amounts of CPU.  It's a known bug but, until it's fixed you have to use top or htop.

As for the fan, how long have you had your laptop?  It may be a simple matter of buying some compressed air and cleaning out all the vents.  If I don't clean my XPS m1330 fans fairly often, the machine becomes noticeably warmer.

---

