---
title: "Why do I have no free memory?"
date: 2007-12-13
forum: Desktop Environments
---

### Post by monstermunch on 2007-12-13
Hi,

I'm running Kubuntu Gutsy. My machine has 2Gb of RAM. When I start up KDE, only about 250Mb is being used by applications. I'm only considering application memory reported by top/ksysguard in this post and ignoring buffers/cached memory (I know that it's a good thing for buffers/cached to use your spare memory).

After doing some really basic things for 40 minutes like checking emails, reading some PDFs and visiting a bunch of websites, I find that I only have about 300Mb of memory free (free as in not used or used by buffers/cached). Here's some output from the console when this happens :

> 
> top

top - 16:39:30 up  5:11,  1 user,  load average: 1.48, 1.08, 0.96
Tasks: 172 total,   1 running, 171 sleeping,   0 stopped,   0 zombie
Cpu(s): 36.1%us,  2.2%sy,  0.3%ni, 60.6%id,  0.0%wa,  0.3%hi,  0.5%si,  0.0%st
Mem:   2062556k total,  2035488k used,    27068k free,   261724k buffers
Swap:  2104472k total,    45036k used,  2059436k free,   383404k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 9244 bob     15   0  429m 143m  30m S   52  7.1  66:49.12 konqueror
18298 bob     16   0  161m  19m  13m S   16  1.0   0:13.44 ksysguard
18300 bob     15   0 32452 1636 1024 S    5  0.1   0:03.24 ksysguardd
 9227 bob     15   0  579m  83m  35m S    2  4.1   3:48.41 amarokapp
 9066 root      15   0  424m 291m 7052 S    1 14.5   4:33.14 Xorg
 9213 bob     15   0 85164 7960 5912 S    1  0.4   3:00.03 artsd
 6300 root      30  15 13408 5152  852 S    0  0.2   0:25.82 preload
18302 bob     15   0  161m  18m  13m S    0  0.9   0:00.55 konsole
...


> free
             total       used       free     shared    buffers     cached
Mem:       2062556    2035200      27356          0     261736     383400
-/+ buffers/cache:    1390064     672492
Swap:      2104472      45036    2059436


Even when I close all my applications (amarok, kwrite, kmail, konqueror, firefox), I only have about 1Gb free. I really just don't understand where all my memory is going and why I don't get it back by closing programs. xorg, amarok and konqueror all say their using 500Mb of "VIRT" memory each (I'm not sure what this means); is this the problem.

Can anyone help? I had the same problem in Feisty and it's really frustrating as I shouldn't be running out of application memory with this much RAM.

---

### Post by Asraniel on 2007-12-13
This isn't bad at all. Linux tries to put everything it can in the RAM, removing unneeded things when there is space needed. RAM should always be full.

---

### Post by monstermunch on 2007-12-13
> **Asraniel said:**
> This isn't bad at all. Linux tries to put everything it can in the RAM, removing unneeded things when there is space needed. RAM should always be full.

Did you read my post?

" I'm only considering application memory reported by top/ksysguard in this post and ignoring buffers/cached memory (I know that it's a good thing for buffers/cached to use your spare memory)."

My _application_ memory isn't being freed up when I close all my user applications  and I'm not running anything demanding that would benefit from using almost 2Gb of memory.

---

### Post by danwood76 on 2007-12-13
can you look into system monitor to see whats eating it all?

It could be a memory leak in something like the flash plugin for firefox, that one always killed my laptop although I think thats fixed now.

---

### Post by rsambuca on 2007-12-13
You have 672MB free.

---

