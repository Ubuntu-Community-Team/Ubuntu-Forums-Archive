---
title: "Fresh install, memory used &gt; 350MB!!   how to reduce?"
date: 2009-01-16
forum: General Help
---

### Post by greylander on 2009-01-16
Hello,

I have a fresh install of Ibex, 8.10, 64-bit, updated, on a machine with 2GB RAM -- 64 bit dual core intel.  Running Gnome.

With no apps running, here is what I get with "free" command:

[INDENT][FONT="Courier New"]greylander@Wraith:~$ free
             total       used       free     shared    buffers     cached
Mem:       2055748     692296    1363452          0      22092     297432
-/+ buffers/cache:     372772    1682976
Swap:      2040212          0    2040212


[/FONT][/INDENT]

Although I have lots of RAM, I really want to maximize available RAM for number crunching application.  And I know ubuntu can run nicely on much less than the 372MB it is using here.

Are there some simple things I can do to get the baseline memory usage down?  I'd like to get back another 200MB if I can.

In the system monitor process list the biggest gobblers are xorg and nautilus.  But really when I look at the list it doesn't seem like the memory used by the processes even fully accounts for the total that I see when I look at the resources tab.

I assume the because I have large 2GB of ram, that ubuntu is not being as conservative with memory as it would be if installed on a machine with much less.  Would there be an easy way to configure it to use ram more conservatively as if much less were availabe?

Any pointers or suggestions greatly appreciated.  Links to useful guides on conserving memory in ubuntu also greatly appreciated.

Thanks!

---

### Post by Yellow Pasque on 2009-01-16
- Google for some Ubuntu optimization guides. You might be able to reduce your memory footprint by eliminating unneeded daemons.
- Try Xfce. It has a reputation for low memory usage. I've found that I'm not missing much by using it over GNOME.
- Add more RAM if possible. You probably have DDR2, which is extremely cheap right now and installing it isn't hard unless you have a case that's a pain to get open. If you need help with determining your RAM type, post back some of your hardware specs (system/motherboard model).

- To see more specific memory usage stats, use:
```
htop
```

---

### Post by KeyserSoze93 on 2009-01-16
As far as I know, ubuntu will always use nearly all the ram, since it uses any free ram for disk write caching.

---

