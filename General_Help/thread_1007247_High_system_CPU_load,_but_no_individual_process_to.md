---
title: "High system CPU load, but no individual process to blame"
date: 2008-12-10
forum: General Help
---

### Post by jaguarul on 2008-12-10
Hi there. I searched the forums for similar posts, but could not find anything useful. Here is my problem:

Every now and then, my system slows down a lot, to the point I have to wait for the cursor to blink, and for characters to appear in my terminal window. This can be several times an hour, for 1-2 minutes.

I see no process eating cpu. Here is the output of 'top' in one of those instances:

```

top - 13:54:14 up 6 days, 20:22,  1 user,  load average: 2.87, 3.07, 2.20
Tasks: 125 total,   2 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.9%us, 45.6%sy,  0.0%ni, 48.8%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   3106696k total,  2973560k used,   133136k free,   161556k buffers
Swap:  4690940k total,    39580k used,  4651360k free,  1148784k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                          
 9520 dragos    20   0  334m 192m  27m S    3  6.3   2:41.01 firefox                                                                                                          
 7550 root      20   0  829m  43m  10m S    2  1.4   2:35.46 Xorg                                                                                                             
 9786 dragos    20   0 80496  24m  12m S    1  0.8   0:01.42 gnome-terminal                                                                                                   
 9385 dragos    20   0 94892  33m  19m S    1  1.1   1:21.82 pidgin                                                                                                           
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.06 init                                                                                                             
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                         
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                      
    4 root      15  -5     0    0    0 S    0  0.0   0:02.66 ksoftirqd/0                                                                                                      
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                       
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                      
    7 root      15  -5     0    0    0 S    0  0.0   0:02.50 ksoftirqd/1                                                                                                      
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                       
    9 root      15  -5     0    0    0 S    0  0.0   0:01.66 events/0                                                                                                         
   10 root      15  -5     0    0    0 S    0  0.0   0:11.42 events/1                                                                                                         
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                          
   46 root      15  -5     0    0    0 S    0  0.0   0:00.22 kblockd/0                                                                                                        
   47 root      15  -5     0    0    0 S    0  0.0   0:00.16 kblockd/1                                                                                                        
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                           
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                     
  141 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                          
  183 root      20   0     0    0    0 S    0  0.0   0:00.30 pdflush                                                                                                          
  184 root      20   0     0    0    0 S    0  0.0   0:06.66 pdflush                                                                                                          
  185 root      15  -5     0    0    0 S    0  0.0   0:00.62 kswapd0                                                                                                          
  226 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                            
  227 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                            
 1475 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                    
 1477 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                            
 1558 root      15  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                                         
 1572 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                                            
 1575 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1                                                                                                            
 1578 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                          
 2384 root      15  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                                      
 2385 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                        
 2423 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                        
 2424 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                                        
 2503 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                                        
 2504 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4                                                                                                        
 2761 root      15  -5     0    0    0 S    0  0.0   0:00.04 reiserfs/0               

```

As you can see, none of the process is eating CPU time, but the 'system' part of the overall load is very high (it varies, and reaches 100% sometimes). These things happen no matter what applications I run. Same if I run KDE instead of Gnome.

I'm using Ubuntu 8.04, nvidia accelerating drivers (desktop effects are off), and I have an Intel Core 2 Duo desktop.
```

$ uname --all
Linux lamppc8 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux
```

How can I find out what's using the 'system' time in what 'top' reports? How can I debug this? 

Thanks!

---

### Post by roccivic on 2008-12-10
Posted something, then realized how stupid it was, so edited out. :P

---

### Post by Thura on 2008-12-10
I have the same problem before ...
It hangs around 10 seconds severl times an hour ..
It really pissed me off when I was watching movies ...
After I compiled the kernel ( from [www.kernel.com](www.kernel.com) without ubuntu patches) myself ... it doesn't happen anymore ...
I don't know why ...
I think this is because of the nvidia driver ...
Before I was using the drivers from the repo, after my custom kernel ... I used the nvidia official installer ...
Try removing all the nvidia drivers you have that you have installed from the repo ..
And install the latest the official package from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) ...

Good Luck !!!

---

### Post by philinux on 2008-12-10
Once it's done the slowdown have a look in Sys>Admin System logs. See if any clues.

---

### Post by jaguarul on 2008-12-10
> **roccivic said:**
> Try leaving gnome-system-monitor run for a while, might even not depend on the CPU, could be lack of RAM and/or SWAP.
Peace

roccivic, thanks for your reply. It doesn't seem to be that, I have 3 Gigs, according to htop and system monitor, there is no swapping (1.5 Gigs used, 0.8% of swap used):

[IMG]http://lamp.epfl.ch/~dragos/files/Screenshot-Terminal.png[/IMG]

I suspect the X server to be guilty party here, but it's only a hunch..

---

### Post by hyper_ch on 2008-12-10
is it an encrypted system?

---

### Post by jaguarul on 2008-12-10
> **Thura said:**
> I have the same problem before ...
...
Try removing all the nvidia drivers you have that you have installed from the repo ..
And install the latest the official package from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) ...

Good Luck !!!

I removed the nvidia accelerated drivers. I'll see if that changes anything.

System logs don't show much. I couldn't find anything strange except this line:

```

Dec 10 15:00:05 lamppc8 ntpd[4559]: can't open /var/lib/ntp/ntp.drift.TEMP: Permission denied

```

I doubt that the network time daemon could slow down things, though..

---

### Post by jaguarul on 2008-12-10
> **hyper_ch said:**
> is it an encrypted system?

Not sure what you mean by that, so I assume it's not. :)

---

### Post by jaguarul on 2008-12-10
> **jaguarul said:**
> I removed the nvidia accelerated drivers. I'll see if that changes anything.


Nope, it still happens randomly.

---

### Post by Thura on 2008-12-10
I was having that problem, since I start using Ubuntu ...
But now ... since last month I don't know why ... it doesn't happen anymore ...
I don't know why ... but I got the impression that is coz I used customized kernel ...

---

### Post by jaguarul on 2009-01-23
> **Thura said:**
> I was having that problem, since I start using Ubuntu ...
But now ... since last month I don't know why ... it doesn't happen anymore ...
I don't know why ... but I got the impression that is coz I used customized kernel ...

Yes, that did it for me as well. I use the Ubuntu server kernel now, and everything seems back to normal. This is not a singular issue, in my lab there's another workstation having the same problem. It's probably a combination of hardware and software.

---

