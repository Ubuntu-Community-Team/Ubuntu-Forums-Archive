---
title: "arts memory usage"
date: 2005-07-09
forum: Desktop Environments
---

### Post by pipodnmy on 2005-07-09
kde has been up for some time on my laptop now, the memory usage shoots way up (512MB with shared video). the problem is that artsd leads all process in terms of memory consumption (it seems) as:
artsd has VmSize of 522,536 (way ahead of all including X - 240,942[shared memory probably], firefox - 124,856)...
about VmRss it comes ony 3rd with 35,788 after X with 99,844 and firefox with 40,448..
should i be disturbed by these according to me very high mem usage of arts or that is expected??
thanks all,

---

### Post by DJ_Max on 2005-07-09
[QUOTE=pipodnmy]kde has been up for some time on my laptop now, the memory usage shoots way up (512MB with shared video). the problem is that artsd leads all process in terms of memory consumption (it seems) as:
artsd has VmSize of 522,536 (way ahead of all including X - 240,942[shared memory probably], firefox - 124,856)...
about VmRss it comes ony 3rd with 35,788 after X with 99,844 and firefox with 40,448..
should i be disturbed by these according to me very high mem usage of arts or that is expected??
thanks all,[/QUOTE]
How much swap do you have freed?

---

### Post by pipodnmy on 2005-07-09
i have 964MB swap with currently 93%free..
i is almost always 100% free

---

### Post by DJ_Max on 2005-07-09
Linux pretty much caches everything, which is why it uses a lot of memory, it frees memory up as needed. You will notice a problem when swap starts to be used considerably. I don't see anything out of the ordinary.

On my small iMac, Xorg uses 25% of memory ( I have 256mb). Firefox uses about 16%, along with other processes.

Right now I have 4mb of free ram, which is normal. I know I'm running fine since I only have 5mb of swap used.

---

### Post by pipodnmy on 2005-07-09
yeap, i know all that.. 
i am fine with all my memory being taken, but i am not sure why artsd would need so much - more than anything else..
if any one has an idea why artsd need so much memory (even for caching or whatever purposes), pls let me know..
to me it sounds quite rediculous..
thanks

---

### Post by DJ_Max on 2005-07-09
Well, what program is arts? I've never heard of it, at least I think...

---

### Post by pipodnmy on 2005-07-09
analog realtime synthesizer, otherwise known the sound deamon in kde:
[http://www.arts-project.org/](http://www.arts-project.org/)

basicly the alternative to esd in gnome..
seems outragous to use that much memory, don't you think?!

---

### Post by magli on 2006-05-15
I now this thread is a year old, but it still seems unresolved to me.

I run kubuntu 6.06 (dapper) on a machineI with 512MB of memory, and 682MB of swap. 

I have had KDE running for several weeks, and the arts daemon is now using 450M of virtual memory, (only 24 of which is resident). 518MB of my 682MB of swap are in use. If I understand things correctly, this means that artsd is using 425MB of my swap. This cannot be normal.

Does anyone know what is going on here?

Thanks,
        
magli

---

### Post by lucifercheff on 2006-08-30
I also have the same problem, Arts uses a large amount of ram. I use a pentum III 700, 448 SDRAM and 200mb swap. Memory is always full and  swap is usually used. Can anybody help us?

---

