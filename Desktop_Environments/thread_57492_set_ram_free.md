---
title: "set ram free"
date: 2005-08-16
forum: Desktop Environments
---

### Post by fahad on 2005-08-16
Hi all,

is there any kind of program in linux to release and free RAM that is not being uses for along time and has been cached ealier, just like some programs in windows .

thanks,
fahad.

---

### Post by DJ_Max on 2005-08-16
Why would you wanna do that. The whole point of having RAM, is to use it, which is what Linux does. Linux isn't Windows. Don't worry unless you start using too much swap.

---

### Post by doclivingston on 2005-08-16
There is no reason to do that - it'll be freed as soon as it's needed for something else.

---

### Post by fahad on 2005-08-17
i have 1 GB of RAM, but after along time of running the system, all the RAM become cached, only a tiny amount of RAM is free

---
MemTotal:       906660 kB
MemFree:          9200 kB
---

notice:
i disabled swap, since i have 1 GB of memory

---

### Post by heimo on 2005-08-17
[QUOTE=fahad]i have 1 GB of RAM, but after along time of running the system, all the RAM become cached, only a tiny amount of RAM is free
[/QUOTE]
That's normal and desired. Memory that is not used, is wasted.


[QUOTE=fahad]
notice:
i disabled swap, since i have 1 GB of memory[/QUOTE]
It wouldn't swap much anyway, but as long as you don't use all your physical memory, this is ok.

---

### Post by fahad on 2005-08-17
OK. 

thanks all for the info. :)

---

### Post by zAo on 2005-08-17
For you information:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          1012        895        117          0         53        532
-/+ buffers/cache:        308        703
Swap:          902          2        899
``` 
It looks like I got 117M free, but as you can see, there is 703M free without the cache/buffers.

Only 2M swap... Windows; can you do that too?  :)

---

### Post by fahad on 2005-08-17
mine:

free -m
             total       used       free     shared    buffers     cached
Mem:           885        879          5          0         31        510
-/+ buffers/cache:        338        546
Swap:            0          0          0

---

### Post by heimo on 2005-08-18
[QUOTE=fahad]mine:

free -m
             total       used       free     shared    buffers     cached
Mem:           885        879          5          0         31        510
-/+ buffers/cache:        338        546
Swap:            0          0          0[/QUOTE]

Run 
 ```
uname -r
or was it 
uname -a

``` 
are you using 386 kernel? You should install 686 (for P4) or K7 (for AMD) kernel. Now you have "only" 900MB recognized, but with correct kernel, you'll get your 1GB. Use Synaptic Package Manager or apt-get (sudo apt-get install linux-686) to install new kernel, don't uninstall the old one, reboot, run uname -a again to make sure it's correct one and run free again to check your total memory.

---

### Post by fahad on 2005-08-18
thanks heimo VERY much  :-) 

the system is now much better because of you,

NOW this is my system info.

free -m
             total       used       free     shared    buffers     cached
Mem:          1012        276        736          0         11        132
-/+ buffers/cache:        132        879
Swap:            0          0          0


 cat /proc/meminfo
MemTotal:      1036504 kB
MemFree:        753784 kB

 uname -a
Linux ubuntu 2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686 GNU/Linux


 \\:D/

---

