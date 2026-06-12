---
title: "Mysteriously high memory usage"
date: 2009-03-20
forum: General Help
---

### Post by FokkerCharlie on 2009-03-20
Hi all

I am seeing very high memory usage on my Ubuntu 8.10 setup.  I see up to around 90% (of 2GB) utilisation, with just Firefox and Thunderbird running in the foreground.

It seems that the memory use starts off reasonably, at around 400 MB, but then gradually increases, throughout the day (typically including a few suspend/resumes) to a high number.

Here's the output from top:
```

top

top - 21:45:16 up 11:26,  2 users,  load average: 6.61, 4.19, 2.25
Tasks: 152 total,   2 running, 150 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.2%us,  2.7%sy,  0.2%ni, 78.5%id,  1.2%wa,  0.1%hi,  0.2%si,  0.0%st
Mem:   2071700k total,  2005064k used,    66636k free,    12612k buffers
Swap:  6072528k total,     5980k used,  6066548k free,   280564k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8959 charlie   20   0  393m 203m  31m S   85 10.1  39:20.97 firefox            
 7672 root      20   0 1235m 1.2g  16m S    4 58.9   9:10.19 Xorg               
 8434 charlie   20   0 72208  44m  19m S    2  2.2   2:40.37 compiz.real        
    1 root      20   0  2384 1196  576 S    0  0.1   0:01.32 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.10 migration/0        
    4 root      15  -5     0    0    0 R    0  0.0   0:00.84 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.12 events/0           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   57 root      15  -5     0    0    0 S    0  0.0   0:01.12 kacpid             
   58 root      15  -5     0    0    0 S    0  0.0   0:00.68 kacpi_notify       
  144 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue             
  148 root      15  -5     0    0    0 S    0  0.0   0:00.18 kseriod            
  193 root      20   0     0    0    0 S    0  0.0   0:00.02 pdflush 
``` 

It looks to me like there is higher than expected memory being used by Xorg, and not all the used memory is accounted for.  So I'd love to know what's going on- any clues?

Cheers
Charlie

---

### Post by 123456789123456789123456 on 2009-03-20
well, you are correct, xorg, seems to be using a whole lot of memory.  could be a case of memory fragmentation.  I know windows has a huge problem with that, but have not encountered such a problem with Ubuntu until now.  does this high accurence start when computer boots, when you open the programs you mentioned?  Does it go back to a normal level when you guit the programs?
I understand it increases during the day.
at this point, without knowing more, it could be a software issue, possible corruption of a file, security problem, that could be fixed with an update.  in some ways it could be related to ram errors in the chips, but I would be hesitent to point to that.  I need some more information, could you test the system memory usage when machine starts up, and after the programs are quit.  even doing some monitoring through several hours, and noting the change in percent of useage, per hour.
It would help diagnose what is accuring, from there we can start to figure out, if it is software or hardware based, and figure a way to repair the situation.

---

### Post by FokkerCharlie on 2009-03-21
Here's what I have found so far:

I ran the memtest utility on the Ubuntu disk, no errors found after 2 passes.

I then booted normally into Ubuntu at 1300, memory use started at 244MB, which gradually rose to 338MB in 5 mins, during which time the only action I took (apart from opening the system resource monitor) was to kill the update notifier process.  The memory use then stabilised.

I started Thunderbird and then Firefox, then closed them both after a few mins at 1325.  Memory use was now showing 562MB.  I then suspended while I went to the shops, and on resume, the computer was using 628MB.

Now (1405), I am using 710MB, with Firefox and Sytem Monitor running.

Any more ideas?

Charlie

---

### Post by Rallg on 2009-03-21
That wouldn't be a problem with your physical memory (computer chips). It sounds like what is known as a "memory leak" in some computer program. Whether it is a system program or (say) Firefox, perhaps due to an add-on, I would not know.

One way to tell if it is Firefox: Quit Firefox, then in System Monitor ensure that no Firefox instances are running. Note memory usage. Do something else for awhile (not on Internet), then check System Monitor again. Memory usage up or down?

---

### Post by FokkerCharlie on 2009-03-22
Right!

Here's a little table of memory use on my laptop.  This is after a re-start, I removed update-notifier from my Sessions, but apart from that it's on my normal setup.  Take a look:

Time  Memory Used (MB)  Remark
1252  249               Immediately after start and login.
1253  266
1257  273
1308  277
1308  277
1311  305
1525  1.4GB.            After a nice walk around the airport.

So, it looks like nothing to do with Firefox or any application like that, but something that I have running all the time, or even something in the OS itself.  

Before I start disabling things to see if I can isolate the problem, could anyone give me a clue as to where to start looking?

Cheers
Charlie

---

