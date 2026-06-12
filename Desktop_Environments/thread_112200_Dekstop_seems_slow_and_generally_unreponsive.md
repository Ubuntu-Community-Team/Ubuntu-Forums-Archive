---
title: "Dekstop seems slow and generally unreponsive"
date: 2006-01-03
forum: Desktop Environments
---

### Post by tms on 2006-01-03
Greetings,

I'm using Ubuntu on my laptop with the following setup:

Prosessor: Intel Pentium -M prosessor 1.7GHz
Chipset: Intel i855PM
Memory: 2 x 512MB PC2700 DDR SDRAM 
Harddrive: Seagate Momentus 40GB 5400RPM (ST94811A)
Graphicscard : ATI MOBILITY Radeon 9700 128MB DDR RAM

So far my Ubuntu experience has been great for the most part, everything worked out of the box , even my soundcard worked on the first boot up which knoppix and slackware failed to configure correctly at installation, kudos for that. 

I have had no problems. Except..the desktop enviorment seems to be generally rather unresponsive, like something's dragging it down. I've had a look at my running services and their usage but I can't see anything which could have such an effect, but I must say, I have an untrained eye.

Here's a cut'n'past of the top command:

```

top - 02:45:44 up 3 min,  2 users,  load average: 0.34, 0.47, 0.21
Tasks: 100 total,   1 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3% us,  0.3% sy,  0.0% ni, 98.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1036136k total,   410068k used,   626068k free,    15180k buffers
Swap:  1951888k total,        0k used,  1951888k free,   229720k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7189 root      15   0  154m  22m 6256 S  1.0  2.3   0:06.74 Xorg
 8306 oddarne   15   0 39660  14m 9776 S  0.3  1.4   0:01.08 gnome-terminal
    1 root      16   0  1564  532  460 S  0.0  0.1   0:01.00 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 events/0
    4 root      17  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   95 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 kblockd/0
  121 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  122 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  124 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  123 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  709 root      15   0     0    0    0 S  0.0  0.0   0:00.04 kseriod
 1923 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 3080 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kjournald
 3206 root      16  -4  1660  568  484 S  0.0  0.1   0:00.06 udevd
oddarne@ubuntu:~$

```

The only thing I can see which might be a part of this is the fact that none of the swap space is used, but I have one gigabyte of memory and there's plenty left so I don't tink that matters. 

I have my harddisk juiced up with dma and the other commands designed to enable some of the settings to speed up the thing, but it gave little to no effect. I also installed the lastet drivers provided by ATI for my gcard, again with little effect. The stepping on my proccessor is working fine according to the various system monitors.

Is this just the way gnome behaves or is there something more to this?

Any help is greatly appreciated.

Later,
TMS.

---

### Post by darkpark on 2006-01-03
my pentium M laptop seems to behave in a similar manner and gnome does seem alittle sluggish but the overall performance is decent.  from my experience, it seems that certain themes (perhaps ones that use lots of colors and textures/pixmaps) seem to slow down gnome.  you might be able to reduce the sluggishness by reducing the bit-depth of the display setting (ie: switch to 16bit colors from 24bit (default)).

---

### Post by soulestream on 2006-01-03
you might want to install the put the "cpu frequency scaling monitor" onto your taskpanel. My laptop is sluggy because it defaults to "ondemand" so 95% of the time my PentM 1.5 is running at 600 MHz.

You can enable the monitor, so you can adjust the speedstep as user. 

[http://ubuntuforums.org/showthread.php?t=76266&highlight=6000](http://ubuntuforums.org/showthread.php?t=76266&highlight=6000) 

I run on "performance" when plugged in. Desktop runs like a champ

soule

---

### Post by tms on 2006-01-03
[QUOTE=soulestream]you might want to install the put the "cpu frequency scaling monitor" onto your taskpanel. My laptop is sluggy because it defaults to "ondemand" so 95% of the time my PentM 1.5 is running at 600 MHz.

You can enable the monitor, so you can adjust the speedstep as user. 

[http://ubuntuforums.org/showthread.php?t=76266&highlight=6000](http://ubuntuforums.org/showthread.php?t=76266&highlight=6000) 

I run on "performance" when plugged in. Desktop runs like a champ

soule[/QUOTE]

Greetings,

That did help. I wasn't aware of that option. Thanks.

Later,
TMS

---

