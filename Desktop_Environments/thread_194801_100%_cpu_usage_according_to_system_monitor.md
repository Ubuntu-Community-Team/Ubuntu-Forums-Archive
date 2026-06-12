---
title: "100% cpu usage according to system monitor?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by codypumper on 2006-06-11
I have 256mb of RAM and an Athlon XP 1.4. Here's a [screenshot]("http://www.flickr.com/photo_zoom.gne?id=165411694&size=o") 
of the system monitor and KDE system guard. I plan to upgrade to 768mb of ram, will it help?

---

### Post by erimar77 on 2006-06-12
eh, it says the "minimum" requirement for memory is 256.. so i'd definately look into getting some more

[http://www.ubuntu.com/download/releasenotes/606?highlight=%28minimum%29](http://www.ubuntu.com/download/releasenotes/606?highlight=%28minimum%29)

---

### Post by vyruss on 2006-06-12
[QUOTE=erimar77]eh, it says the "minimum" requirement for memory is 256.. so i'd definately look into getting some more[/quote]

More RAM always helps, but if you want to know I have two default desktop installations working perfectly, one in a PII with 192mb and the other in a clamshell G3 iBook with 128mb! Both of them show 0% cpu when idle.

I think something else is wrong here. **codypumper**, are you sure your system wasn't running updatedb in the background or anything? I've also seen that the flash plugin, when you have several firefox windows open, can reach 100% cpu. Does your system reach 100% with no programs running, on idle?

---

### Post by Juippisi on 2006-06-12
And when that happens, open up a terminal and type "top". See what process is eating your CPU. I believe you can see that process also from the system-monitor at the "Processes" tab.

---

### Post by codypumper on 2006-06-12
Thanks for the support! When I type top in terminal I get:

top - 11:53:19 up 1 day, 14:40,  2 users,  load average: 2.88, 2.68, 2.48
Tasks:  90 total,   3 running,  86 sleeping,   0 stopped,   1 zombie
Cpu(s): 17.6% us, 82.1% sy,  0.0% ni,  0.0% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:    248296k total,   243100k used,     5196k free,     2820k buffers
Swap:   722884k total,   199392k used,   523492k free,    50176k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3001 root      23  -2  1580  352  352 R 80.4  0.1   2057:25 modprobe
12447 root      15   0  111m  39m 4644 S 11.0 16.2  30:52.18 Xorg
 5425 pumpers   15   0 40152  14m 9056 S  7.0  5.8   0:01.97 gnome-terminal
 1905 root      10  -5     0    0    0 S  0.3  0.0   0:13.65 usb-storage
12457 pumpers   16   0 19556 4992 4520 S  0.3  2.0   0:01.80 x-session-manag
12516 pumpers   16   0 15452 6696 5276 S  0.3  2.7   0:32.28 metacity
12598 pumpers   15   0  582m  93m  18m S  0.3 38.4  43:44.21 firefox-bin

---

### Post by barakaspeed on 2006-06-13
What is your kernel verison?  $uname -r

This is something I stumbled upon that has helped me:

[http://www.ubuntuforums.org/showthread.php?t=194833](http://www.ubuntuforums.org/showthread.php?t=194833)

---

### Post by codypumper on 2006-06-13
My kernel version is 2.6.15-23-386

---

### Post by vyruss on 2006-06-14
[QUOTE=codypumper]My kernel version is 2.6.15-23**-386**[/QUOTE]

OK, I'm going offtopic here, but it is highly unlikely that you have a Pentium-class or lower machine. Why don't you try changing the kernel to one optimized for your machine?

If you have an Athlon or similar AMD processor, use the **-k7** kernel.
If you have an Intel PII/III/4-class, use the **-686** kernel.

The packages you need to install from **synaptic** are:

**linux-k7** or **linux-686**, respectively.

This might not fix your problem, but it will give you better performance.
For a fix, I suggest you take a look at the bug reports for the kernel package in **launchpad.net**.

---

### Post by codypumper on 2006-06-14
Is the optimized kernel updated?

---

### Post by vyruss on 2006-06-14
[QUOTE=codypumper]Is the optimized kernel updated?[/QUOTE]

It should be current as of June 1, 2006, but I'm not sure that the kernel is your problem really. However, it would be to your benefit to use the **-k7** kernel, since you're using an Athlon. Why don't you try it and tell us what happens?

Also, it would be helpful if you could give us a screenshot of **System Monitor** when you have selected the **Processes** tab and you have clicked on **% CPU** so that System Monitor sorts the processes from highest CPU usage to lowest, and shows us what process consumes all the CPU power.

---

### Post by codypumper on 2006-06-15
The -k7 kernel isnt in synaptic

---

### Post by codypumper on 2006-06-15
Wait a sec....my cpu is at 5%?!? Thanks for your help guys, but I think they patched the problem, and I'm gonna guess it was the system monitor was jacked up. THanks again!

---

### Post by vyruss on 2006-06-15
[QUOTE=codypumper]The -k7 kernel isnt in synaptic[/QUOTE]

Type```
sudo gedit /etc/apt/sources.list
```in a terminal and make sure you include the following lines in that file:```
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```

---

