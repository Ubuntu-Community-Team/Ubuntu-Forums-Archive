---
title: "Kubuntu Desktop using TOO much memory"
date: 2009-03-05
forum: Desktop Environments
---

### Post by MaquinaX on 2009-03-05
Hello Everyone,
                Lately I've noticed that when ever a program is asking for a little more out of the system (when Amarok is importing library), the system just hangs for about 10 minutes. At first I thought it was a but with Amarok,
but then I discovered that it happens whenever ANY program is taking up more memory than usual. I'm running Kubuntu 8.04. I have 1G of memory in my system, and this is not an issue with by Ubuntu desktop running 7.10. I then restarted my Kubuntu desktop, and it turns out that it's using 800mb of memory !!! right out of start up. Where is all my memory going to? If anybody can help, I would greatly appreciate it. 

Thanx,

MaquinaX

---

### Post by skymera on 2009-03-05
Can you run `top` in the Terminal (Konsole?)

Post the output.

---

### Post by MaquinaX on 2009-03-06
I guess it's using more then what I expected, but where is it all going. Is it a bug?

MaquinaX

### Top Result ###
top - 22:15:31 up 3 days, 8 min,  1 user,  load average: 0.19, 0.11, 0.09
Tasks: 119 total,   2 running, 117 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.7%us,  1.7%sy,  0.0%ni, 89.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035364k total,   934796k used,   100568k free,   326184k buffers
Swap:  5807456k total,    39952k used,  5767504k free,   462448k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5530 root      20   0 47004  30m 5068 S  4.3  3.0   2:59.43 Xorg
16452 jose      20   0 32596  13m  11m S  0.7  1.4   0:05.30 kded
16460 jose      20   0 29608  11m 8884 S  0.7  1.1   0:07.00 kwin
16464 jose      20   0 32824  14m  11m S  0.7  1.4   0:06.58 kdesktop
16469 jose      20   0 36556  18m  13m S  0.7  1.8   0:06.58 kicker
16505 jose      20   0 24316  12m  10m S  0.7  1.2   0:01.80 kde-window-deco
23829 jose      20   0 33728  15m  11m R  0.7  1.5   0:01.30 konsole
23890 jose      20   0 39752  21m  16m S  0.7  2.2   0:00.84 kate
23909 jose      20   0  2304 1116  856 R  0.7  0.1   0:00.32 top
    1 root      20   0  2844 1692  544 S  0.0  0.2   0:01.26 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:01.56 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.94 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
   41 root      15  -5     0    0    0 S  0.0  0.0   0:01.04 kblockd/0

---

### Post by MaquinaX on 2009-03-07
ttt

---

### Post by MaquinaX on 2009-03-09
anyone?

---

