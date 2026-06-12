---
title: "lxdream - Dreamcast Emulator for Linux"
date: 2007-11-03
forum: Gaming &amp; Leisure
---

### Post by RemmyLee on 2007-11-03
From the site:> 
Lxdream is a linux-based emulator for the Sega Dreamcast system. While it is still in heavy development (and many features are buggy or unimplemented), it is already capable of running many demos and some games.

Link: [lxdream]("http://www.lxdream.org/news/")

---

### Post by BigSilly on 2007-11-03
That excellent! Thanks for letting us know. 

I think a DC emulator is all that's really missing from Linux. Hopefully this'll fit the bill.

---

### Post by wishyjr on 2007-11-04
have you guys managed to successfully install it? im having a problem compling it. I get an error telling me the esound package is not installed btu having checked synaptic  - it is!

any ideas?

---

### Post by Ferrat on 2007-11-04
> **wishyjr said:**
> have you guys managed to successfully install it? im having a problem compling it. I get an error telling me the esound package is not installed btu having checked synaptic  - it is!

any ideas?

Sounds like a version mismatch or typo

---

### Post by robertobech on 2007-11-08
Same problem here, except that I'm running CentOS 5, but I guess our problems will be solved the same way.

---

### Post by robertobech on 2007-11-08
Hmmm... just found this:

[http://www.lxdream.org/forums/viewtopic.php?t=30](http://www.lxdream.org/forums/viewtopic.php?t=30)

---

### Post by lunarcloud on 2007-11-15
where does the bios go?

and i compiled it and only get...
```
sam@zempharia:~/Downloads/lxdream-0.8.1$ lxdream
13:51:43 00000000 ERROR Unable to load file '(null)': &#65533;&#65533;f&#65533;tD&#65533;&#65533;H&#65533;$H&#65533;lL&#65533;d$H&#65533;&#65533;&#9618;&#65533;H&#65533;}
13:51:43 00000000 ERROR --- Aborting with signal 11 ---
Using host libthread_db library "/lib/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread 47948420207632 (LWP 11277)]
0x00002b9bdac09c05 in waitpid () from /lib/libc.so.6
#0  0x00002b9bdac09c05 in waitpid () from /lib/libc.so.6
#1  0x00002b9bdabad831 in ?? () from /lib/libc.so.6
#2  0x0000000000442da1 in report_crash (signo=<value optimized out>, info=<value optimized out>, ptr=<value optimized out>) at util.c:46
#3  <signal handler called>
#4  0x00002b9bdabe8b30 in strlen () from /lib/libc.so.6
#5  0x00002b9bdabb725a in vfprintf () from /lib/libc.so.6
#6  0x00002b9bdabb8143 in ?? () from /lib/libc.so.6
#7  0x00002b9bdabb3a7e in vfprintf () from /lib/libc.so.6
#8  0x000000000044239f in log_message (ptr=<value optimized out>, level=1, source=<value optimized out>, msg=0x445a8e "Unable to load file '%s': %s") at util.c:306
#9  0x000000000040ac7d in mem_load_block (file=0x747940 "dcflash.rom", start=2097152, length=131072) at mem.c:201
#10 0x000000000040fb14 in dreamcast_configure () at dreamcast.c:73
#11 0x000000000040fb69 in dreamcast_init () at dreamcast.c:123
#12 0x0000000000409b75 in main (argc=1, argv=0x7fffd422e958) at main.c:129
Aborted (core dumped)
```

---

### Post by xjgnsdof on 2007-11-17
You put the bios files wherever you want and tell the program where to look for them--I believe that you do so in the "paths" option in the main menu.

I've configured, made, and compiled this thing with esound installed and bios files situated, but I get missing polygons and no sound in the game. This is unusual given my system specs and the fact that the Dreamcast boot screen music plays each time.

I have another thread on this, but has anyone gotten Shenmue 1 to not only work, but play perfectly?

---

