---
title: "after 1-2 hours, processors permanently on &gt;70% load"
date: 2010-06-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jdelgado on 2010-06-10
Hi there,

I installed 10.04 recently. Now, after one or two hours of normal workload, the processors start to be loaded at 80% just for opening a small text file of any other small operation, like opening the terminal.

If I turn off and then on again, it still present the same problem. When it gets a night sleep, then it works fine again for 1-2 hours.

I have a dell latitude d630 with 32 bit lynx.

What is going on? even writing this thread took ages!

thanks for your help.

ze

---

### Post by arrange on 2010-06-10
After the two hours:
What does the command *top* say in [Terminal](https://help.ubuntu.com/community/GnomeTerminal)?  Which process(es) take up the most CPU?

Could you also provide your memory situation?```
free -m
```

---

### Post by jdelgado on 2010-06-10
Hi,

well, top shows that everything is ok, nothing is really above 2 or 3 %, except when I open a folder, start a small application like gedit or firefox, then it reaches 90-100%. The system is in general very slow. What thrills me is that if I restart it it stays the same. right now the first lines of top are:
> 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1784 jdelgado  20   0  216m  60m  25m R   36  1.5   2:53.00 firefox-bin        
  972 root      20   0 53596  18m 8240 R   28  0.5   2:40.18 Xorg               
 1664 jdelgado  20   0 47680  13m  10m S   26  0.3   0:19.56 gnome-terminal     
 1813 jdelgado  20   0  2544 1228  924 R    4  0.0   0:01.86 top                
 1651 jdelgado  20   0 40700  19m 5148 S    2  0.5   0:20.76 ubuntuone-syncd    
  879 avahi     20   0  3184 1696 1272 S    1  0.0   0:02.82 avahi-daemon       
 1445 jdelgado  20   0 20372  10m 8452 S    1  0.2   0:06.81 metacity           
 1502 jdelgado  20   0 31892  13m  10m S    1  0.3   0:00.92 clock-applet    



that's my memory situation:
>              total        used       free     shared    buffers     cached
Mem:          4026        524       3502          0         23        262
-/+ buffers/cache:        238       3788
Swap:         3035          0       3035


thanks

ze

---

### Post by jdelgado on 2010-06-10
the CPU processes seem fine to me...

I have tried

metacity --replace

compiz --replace

nothing new happened. I have tried to remove Ubuntu One, Gwibber, and couchdb, as suggested in other threads, and Igot nothing new...

My laptop is way too slow to get any work done since I left karmic!

:confused:

---

### Post by arrange on 2010-06-10
Hmm, this is a bit confusing for me... Sometimes you write it's slow all the time, sometimes 2 hours from the start... Or - when you start an application - it's pretty normal that it takes some CPU for a few moments. Or - the thread title says it's _permanent_ > 70% load, but *top* doesn't show that...

So - what is actually slow? Opening applications, moving windows around,...? Can you narrow it down a little?

---

