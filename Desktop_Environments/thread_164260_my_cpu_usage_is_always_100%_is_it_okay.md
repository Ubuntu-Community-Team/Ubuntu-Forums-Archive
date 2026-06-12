---
title: "my cpu usage is always 100% is it okay?"
date: 2006-04-22
forum: Desktop Environments
---

### Post by medya on 2006-04-22
during the last 48 hours my pc has been ON and Downloading stuff from internet, it is the first time that I let my PC be on all the time...

I checked the CPU uages in ubuntu, and it has been CONSTANTLY 100% .
isnt it dangrous ? 
my cpu is 2 GHZ Intel Celeron. wont it damage my cpu ? i just worry.


by the way, can you please post your cpu usage in ubuntu too ?

---

### Post by Ramses de Norre on 2006-04-22
This certainly isn't normal, my cpu load is about 4% when using amarok, amsn, firefox.
You can use the top command to check which processes are using so much cpu.

---

### Post by medya on 2006-04-22
hey I guess the system monitor is showing wrong...

the system monitor is showing 100% usage of cpu almost always.

but the top command shows like 44 % usage look at the top command result

> top - 21:57:38 up 15:35,  2 users,  load average: 3.69, 3.43, 3.11
Tasks: 108 total,   4 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s): 52.8% us, 47.2% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    256784k total,   247192k used,     9592k free,     4336k buffers
Swap:   208804k total,   110124k used,    98680k free,    85188k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
18630 fred      25   0 14500 7736 5904 R 34.4  3.0  42:52.73 zenity
19194 fred      25   0 14504 7556 5736 R 31.7  2.9   1:14.08 zenity
 8021 root      15   0  107m  24m 9864 S 18.1  9.8 104:58.63 Xorg
19209 fred      15   0 31824  13m 8492 S 10.1  5.2   0:04.93 gnome-terminal
19115 fred      16   0  124m  45m  16m R  2.1 18.2   4:06.53 firefox-bin
18769 fred      15   0 59592  15m 9.8m S  1.3  6.1   0:26.21 beep-media-play
 8757 fred      15   0 19080 8488 7264 S  1.1  3.3   1:44.02 geyes_applet2
 7564 hal       17   0  1872  444  428 S  0.3  0.2   0:05.54 hald-addon-stor
 8217 mysql     16   0  113m 1816 1000 S  0.3  0.7   0:05.91 mysqld
 8704 fred      15   0 15404 8328 6100 S  0.3  3.2   2:22.33 metacity
 8747 fred      16   0 19656 8220 6788 S  0.3  3.2   0:09.00 fish-applet-2
 8771 fred      15   0 21584  10m 8064 S  0.3  4.2   0:45.19 stickynotes_app
19223 fred      16   0  2136 1112  844 R  0.3  0.4   0:00.17 top
    1 root      16   0  1564  472  444 S  0.0  0.2   0:01.27 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.37 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   84 root      10  -5     0    0    0 S  0.0  0.0   0:00.73 kblockd/0
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.43 pdflush
  115 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  114 root      15   0     0    0    0 S  0.0  0.0   0:01.38 kswapd0
  700 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kseriod
 2369 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 3957 root      15   0     0    0    0 S  0.0  0.0   0:02.68 kjournald
 4099 root      12  -4  1664  428  424 S  0.0  0.2   0:00.23 udevd
 6989 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 7491 root      16   0  1824  520  516 S  0.0  0.2   0:00.00 acpid
 7523 root      15   0  1564  340  320 S  0.0  0.1   0:00.65 dd
 7525 klog      15   0  2472  508  464 S  0.0  0.2   0:00.34 klogd
 7538 messageb  16   0  2148  640  636 S  0.0  0.2   0:00.05 dbus-daemon
 7551 hal       16   0  5068 1560 1288 S  0.0  0.6   0:00.78 hald
 7556 hal       19   0  1868  392  388 S  0.0  0.2   0:00.00 hald-addon-acpi
 7566 hal       16   0  1868  556  520 S  0.0  0.2   0:02.25 hald-addon-stor
 7938 root      16   0 11340 1396 1392 S  0.0  0.5   0:00.00 gdm
 7947 root      16   0 11668 1584 1552 S  0.0  0.6   0:02.86 gdm
 8080 hplip     18   0  4416  756  752 S  0.0  0.3   0:00.00 hpiod
 8180 root      23   0  2596 1000  996 S  0.0  0.4   0:00.00 mysqld_safe
 8216 root      23   0  2596 1012 1008 S  0.0  0.4   0:00.00 mysqld_safe
 8218 root      15   0  1548  432  428 S  0.0  0.2   0:00.00 logger
 8265 fred      15   0 18780 6112 5676 S  0.0  2.4   0:02.58 x-session-manag
 8366 fred      16   0  3124  540  516 S  0.0  0.2   0:00.01 ssh-agent
 8369 fred      15   0  2572  616  612 S  0.0  0.2   0:00.00 dbus-launch
 8370 fred      15   0  2148  700  632 S  0.0  0.3   0:00.00 dbus-daemon
 8379 fred      16   0 14416 5244 1672 S  0.0  2.0   0:03.77 gconfd-2
 8514 debian-t  16   0 12816  10m 1396 S  0.0  4.2   0:29.01 tor


---

### Post by GeneralZod on 2006-04-22
[QUOTE=medya]hey I guess the system monitor is showing wrong...

the system monitor is showing 100% usage of cpu almost always.

but the top command shows like 44 % usage look at the top command result[/QUOTE]

No, it's showing 100% - you need to add up all the figures on this line (except for "id" - "idle"), or simply subtract the idle% from 100% (in this case, 100% - 0% = 100%).

Cpu(s): 52.8% us, 47.2% sy, 0.0% ni, **0.0% id**, 0.0% wa, 0.0% hi, 0.0% si

In you case, the two instances of "zenity" are using up the most (and they shouldn't be, so they've gone wrong and locked up or something).  I'm sure I've seen this exact problem before - I'll try and find the thread.

Edit:

Nope - can't find it - sorry! :)

---

### Post by Ramses de Norre on 2006-04-22
@ GeneralZod: maybe I found someone who knows what all the percentages mean, do you know what the last one means? The one with 'si' after?

@ medya: I don't really know about the zenity, but xorg is using a lot of your cpu too. It uses only 1% at my system.. Maybe using another theme could help (I've seen themes that made xorg use a lot of cpu here too).

---

### Post by GeneralZod on 2006-04-22
[QUOTE=Ramses de Norre]@ GeneralZod: maybe I found someone who knows what all the percentages mean, do you know what the last one means? The one with 'si' after?[/QUOTE]

I don't know for sure, but it seems that top derives some of its output from "vmstat", in which case:

```

$ man vmstat | grep si
    si: Amount of memory swapped in from disk (/s)

```

---

### Post by medya on 2006-04-22
oh my god, so my cpu has been using 100% of its power for the last 24 hours?
hm... I wonder why Linux didnt hang... in windows when the cpu uses 100% the system crushes....

it can be a Bad Aspect of ubuntu's power (even though it was using 100% of the cpu it didnt crush)
I worry that my cpu have been damaged... anybody knows about the hardwares ... have my cpu been damaged ?

by the way what is Xorg and whats is zenity ?

---

### Post by GeneralZod on 2006-04-22
[QUOTE=medya]oh my god, so my cpu has been using 100% of its power for the last 24 hours?
hm... I wonder why Linux didnt hang... in windows when the cpu uses 100% the system crushes....

it can be a Bad Aspect of ubuntu's power (even though it was using 100% of the cpu it didnt crush)
I worry that my cpu have been damaged... anybody knows about the hardwares ... have my cpu been damaged ?
[/QUOTE]

CPU's are designed to be hammered pretty hard, and to last for years under continuously heavy load.  Google (at one point, and probably still now) used to run their servers on commodity hardware, such as you and I have, 24/7, and you can imagine how hard Google's servers must work :) My Windows machine at work has been running Folding@Home 24 hours a day at 100% CPU for a year and a half now.  In short, practically zero chance of damage, but zenity is obviously buggy and shouldn't be using anywhere near that amount of CPU.  You should probably do a 

```

killall zenity

```

> 
by the way what is Xorg and whats is zenity ?

[http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)
[http://directory.fsf.org/zenity.html](http://directory.fsf.org/zenity.html)

:)

---

### Post by medya on 2006-04-22
I found out how that Zenity is made, it is made by Automatix program , automatix has alwasy been my ubuntu's enemy, I have re-installed my whole ubuntu three times, just because automatix broked my ubuntu.

each time I promise myself not to use automatix, but unfortuantly I am too lazy to insall codecs so I break my promise.

+ thanks for "Killall zenity" command,  zenity in automatix is used for the windows which shows what program is being installed right now.

I hope my killing that , dont affect autoamtix's job... (it is still downloading codecs and stuff...)

---

### Post by medya on 2006-04-22
now my cpu usage is 4% and ubuntu is so much faster...

---

### Post by aristotlewilde on 2007-05-17
I have a very similar issue when I run Folding at Home...  

I had to disable it as a result.

---

