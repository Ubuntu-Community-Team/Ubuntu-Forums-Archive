---
title: "Performance problems Cedega / Hoary - Counter Strike Source"
date: 2005-07-08
forum: Gaming &amp; Leisure
---

### Post by Soulfly on 2005-07-08
Hi

This was originally a plea on the transgaming forums: [http://transgaming.org/forum/viewtopic.php?p=19273#19273](http://transgaming.org/forum/viewtopic.php?p=19273#19273)

I have performance problems with the most recent CSS-maps: de_inferno, de_assault (7-9 fps), other maps such as de_dust and de_prodigy are running okay. The only person responded to my thread above had the same problems as me, was running Ubuntu and didn't see the same problems in Windows. I started this thread because Ubuntu is the common denominator for us and some hope that some of you have solved this (i've tried to search both google and this forum).

My specs:
Normal Ubuntu 5.04 install (i use to run the lightweight ion3 windowmanager in vt7 with licq and TeamSpeak while running css in vt8   )
Linux version 2.6.11 (root@salsa) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Sat Jun 11 17:16:58 CEST 2005
(**) |   |-->Device "NVIDIA Corporation NV36 [GeForce FX 5700 LE]"
Driver:  NVIDIA-Linux-x86-1.0-7664-pkg1.run
Cedega package version:  4.3.2-1
cpuinfo:model name      : AMD Athlon(tm) XP 2500+
cpuinfo:cpu MHz         : 1837.387
cpuinfo:cache size      : 512 KB
MemTotal:      1036084 kB


has anyone seen these problems or have any solution to our performance problems?



In the following thread there is a number of good tips on improving on CSS performance: 
[http://transgaming.org/forum/viewtopic.php?t=1926](http://transgaming.org/forum/viewtopic.php?t=1926)

I've tried most of them without any improvement. I tried to compile xorg and glibc optimized for my processor with apt-build. However, apt-build didn't use my settings in the compilation, here's my config-file:
```

$ cat /etc/apt/apt-build.conf
build-dir = /var/cache/apt-build/build
repository-dir = /var/cache/apt-build/repository
Olevel = -O2
march = -march=athlon-xp
mcpu = -mcpu=athlon-xp
options = " -funroll-loops -pipe "

```

I realise I can improve perfomance by recompiling xorg (according to above thread, and others) optimized to my processor. Anyone knows what i'm doing wrong with apt-build [my options/arch/cpu isn't forwarded to the actual compile] ?

---

### Post by dclaridge on 2005-07-22
Ive been running it on windows and get the same issue - those maps are buggy

---

### Post by Seer on 2005-07-25
[QUOTE=Soulfly]
 was running Ubuntu and didn't see the same problems in Windows. [/QUOTE]

A map file is a map file, a texture file is a texture file regardless of the OS  so.....

[quote=dclaridge]those maps are buggy[/quote]

is actually not true!

Either Linux or Cedega is doing a crap job with some gfx features used a lot in those maps.

---

