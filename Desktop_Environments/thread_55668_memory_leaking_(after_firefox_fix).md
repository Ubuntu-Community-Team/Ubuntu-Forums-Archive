---
title: "memory leaking (after firefox fix)"
date: 2005-08-09
forum: Desktop Environments
---

### Post by spudley on 2005-08-09
Can anyone assist in helping me find a memory leak?

I've only got 384Mb installed... every day my % memory used increases (not so much/quickly after the firefox fix)... but swap increases and so does regular memory.  Every few days I need to reboot the machine or its all at 100% used.

My machine sits running firefox w/ a number of tabs open, 2 gdesklets open (weather & a monitoring panel).  SETI @ home, Rythm Box runs occassionaly and sometimes an OpenOffice document and thats it... it is on my network (but not as a file server - workstation with mounted network drives only).  Its a pretty 'simple' setup at present -- but its my test machine for Ubuntu before I deploy it across the rest of my network workstations & I need the bugs out first.

Thanks!

---

### Post by PeP on 2005-08-09
[QUOTE=spudley]Can anyone assist in helping me find a memory leak?

I've only got 384Mb installed... every day my % memory used increases (not so much/quickly after the firefox fix)... but swap increases and so does regular memory.  Every few days I need to reboot the machine or its all at 100% used.

My machine sits running firefox w/ a number of tabs open, 2 gdesklets open (weather & a monitoring panel).  SETI @ home, Rythm Box runs occassionaly and sometimes an OpenOffice document and thats it... it is on my network (but not as a file server - workstation with mounted network drives only).  Its a pretty 'simple' setup at present -- but its my test machine for Ubuntu before I deploy it across the rest of my network workstations & I need the bugs out first.

Thanks![/QUOTE]


it is normal !
you have memory, then the system uses it, the memory keeps a copy of the files in your disk even when you do not use it so that it can re-open it quickly next time you want to use it.

when it lacks memory, linux first move the least used memory pages to swap and then deletes it from memory.
a memory leak is what happens when one application use more and more memory until it crashs. use top/ksysguard/gnome equivalent to follow that and file a bug for the application.

---

### Post by coolclassic on 2005-08-09
Can you give us a top read out.


If you suspect firefox try another browser.

---

### Post by spudley on 2005-08-09
Here's the output of my top.... regular memory is a big down since my orginal post, but the swap use is still climbing (and I haven't used the machine since that first post)

```
top - 21:00:24 up 4 days,  1:27,  2 users,  load average: 0.62, 0.45, 0.62
Tasks:  86 total,   3 running,  83 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.1% us, 13.0% sy, 67.3% ni, 10.3% id,  0.0% wa,  0.1% hi,  0.2% si
Mem:    386900k total,   380524k used,     6376k free,    12156k buffers
Swap:   465844k total,   375764k used,    90080k free,   135732k cached
 Unknown command - try 'h' for help
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6600 ernie     15   0  419m  96m 8404 S  9.8 25.6 321:19.31 python
30717 ernie     15   0  112m  48m  17m S  5.9 12.9   5:32.72 firefox-bin
12642 ernie     15   0 79120  16m  10m S  5.9  4.5   9:03.94 rhythmbox
 5438 root      15   0 99.8m  37m 6768 S  3.9 10.0 729:08.06 Xorg
15680 ernie     15   0  2076  952  736 R  2.0  0.2   0:00.01 top
    1 root      16   0  1552  464  440 S  0.0  0.1   0:00.76 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.03 ksoftirqd/0
    3 root       5 -10     0    0    0 S  0.0  0.0   0:00.09 events/0
    4 root       6 -10     0    0    0 S  0.0  0.0   0:00.02 khelper
   22 root      15 -10     0    0    0 S  0.0  0.0   0:00.00 kacpid
   79 root       5 -10     0    0    0 S  0.0  0.0   0:00.43 kblockd/0
  114 root      15   0     0    0    0 S  0.0  0.0   0:00.12 pdflush
  115 root      15   0     0    0    0 S  0.0  0.0   0:00.17 pdflush
  117 root      13 -10     0    0    0 S  0.0  0.0   0:00.00 aio/0
  116 root      15   0     0    0    0 S  0.0  0.0   0:02.64 kswapd0
  704 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1072 root      15   0     0    0    0 S  0.0  0.0   0:08.23 kjournald

```


Obviously python for gdesklets (I assume) is using a fair bit... I wonder if its a gdesklets problem?  I use good weather and several "FTP" monitors (FTP-CPU gauge, memory plot and others).

---

### Post by varunus on 2005-08-09
Last I heard, gdesklets did have some memory leaks.  (Some desklets do, at least.)  Though, I don't know if they fixed it, I stopped using gdesklets a few months back; went the "panel applet" approach instead, since its always visible.  (CPU/memory monitors are available, as is a weather applet.)  It may not look as pretty, but i like the compact out-of-the-way nature.

---

### Post by coolclassic on 2005-08-09
Python seems to be taken a lot of resources

---

### Post by spudley on 2005-08-09
[QUOTE=varunus]I stopped using gdesklets a few months back; went the "panel applet" approach instead[/QUOTE]

Varunus,  are there panel applets available for install other than the ones I see on right clicking the panel?

The problem must be gdesklets.. I checked it, again.. my swap was almost 100% used... python for gdesklets was showing 450 or so Mb in VM size... I killed the gdesklets daemon and memory went down to only about 12% used.  A restart of gdesklets and memory used is only 30% used now.

I'll have to keep an eye on it - unfortunately, I like the eye candy ;)

---

### Post by varunus on 2005-08-10
I haven't found that many panel applets, unfortunately.  Everything I needed, at least, GNOME came with an applet for though; there's a weather applet and a CPU/Memory/Temperature/Everything monitor applet (add system monitor to the panel in the right click menu).  I'm working on learning how to use libpanelapplet; are there any applets you would like, specifically?  I need a project to learn with anyway... :)

---

