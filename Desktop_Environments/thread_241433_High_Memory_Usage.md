---
title: "High Memory Usage"
date: 2006-08-22
forum: Desktop Environments
---

### Post by AquaFox90 on 2006-08-22
Hello,

Yesterday late at night when before I switched off my computer I Ctrl+Esc to find out how much RAM I was using and I used A WHOLE 2 GB RAM of my 1.5GB RAM.

I am running KDE and I have simple programs running like Konqueror, KTorrent, XChat. The highest memory usage is artsd :confused: ..

Is this memory leaks or what is happening :x?

I don't usually switch off my computer. May once every two days.

Help plx.

---

### Post by az on 2006-08-22
Unused ram is wasted ram.  Usually, the cached ram is dumped if another process needs it.

---

### Post by Lord Illidan on 2006-08-22
By running free in a terminal, you can see how much of your memory is actually cached or really being used up.

---

### Post by AquaFox90 on 2006-08-22
Sorry.. I am using 1 GB that was a typo. When I start my computer I am using 350 MB not 1 GB? Can you please tell me how come so much RAM? And so what if it dumps some RAM that shouldn't make RAM usage so high.

---

### Post by az on 2006-08-22
> **AquaFox90 said:**
> Sorry.. I am using 1 GB that was a typo. When I start my computer I am using 350 MB not 1 GB? Can you please tell me how come so much RAM? And so what if it dumps some RAM that shouldn't make RAM usage so high.

Why should it dump it if it is not bothering anybody?  

To be most efficient, you should not dump any ram until you run out of it.

---

### Post by ajgreeny on 2006-08-22
Yes, really, everyone is telling you what happens in linux for memory management.  Anything the software puts in ram stays there until such time as there is no room left and then the oldest info that is not currently needed is removed.  This is one reason why you will seldom hear the hard drive swapping info in a linux system; it seldom needs to.  I have 1Gb ram on my machine but when I installed the system, the default was to give me over 2 Gb of swap.  To the best of my knowledge I have never used any of that swap.

At this minute *free -m* shows:-

andrew@kubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        739        271          0         81        459
-/+ buffers/cache:        197        812
Swap:         2965          0       2965
andrew@kubuntu:~$

You will see only 271 Mb free and 739 used of my 1Gb (actually 1010 Mb as linux kernel sits in some ram all the time). I ony have firefox open at the moment.  The more important figure is the 197 in -/+ buffers/cache: which is the amount of ram being used by what is running at the moment.

Don't get hung up on apparent memory usage.  It's just how things happen in linux and it works wonderfully!

---

### Post by tribaal on 2006-08-22
If you still have questions regarding this, you might want to give the link in my signature a try.

- trib'

---

### Post by oobuntoo on 2006-08-23
I don't usually look at how much of my ram is being used as long as  my system runs smoothly. Recently my system started using swap space so I looked and found out that only about 25MB of 1GB RAM is free. The problem is not that any particular program is using too much memory. XGL uses the most at about 150MB, which I think is reasonable. The problem, I think, is that there are too many processes running. I'm running Kubuntu 6.06 and there are about 122 processes running. I don't know if this is normal. Is there a resource somewhere that can help determine which of these processes can be safely killed and stopped from running?

---

### Post by ajgreeny on 2006-08-23
Have a look at bum from the repos. or if you like the command line follow the txt file attached.  I imagine most of the 122 processes are sleeping so won't be using ram, but it seems a lot of processes.  My comp has 97 running in total.

---

