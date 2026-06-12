---
title: "Ubuntu's sucking my memory for some reason"
date: 2006-02-05
forum: Desktop Environments
---

### Post by aysiu on 2006-02-05
Ubuntu's been just fine for the past nine months I've been using it.

All of a sudden, this past week, it's been sucking up my memory. 512 MB has been sufficient before, but now it's all sucked up. At first I got really paranoid and thought someone had breached my system and set up some weird process, but unplugging my internet didn't make a difference, nor did an entirely complete reinstallation of Ubuntu.

Okay. It gets weirder. I do a dual-boot with Windows. No sluggishness in Windows whatsoever.

Weirder still: I booted up Knoppix, and it doesn't use as much memory as Ubuntu is currently doing (keep in mind--Ubuntu was fine for nine months straight). This is the *top* command in Knoppix using the live CD (that's right--no hard drive use--all CD and RAM) with Mozilla, Konqueror, GIMP, and Konsole running: ```
top - 21:18:43 up 3 min,  0 users,  load average: 0.54, 0.31, 0.12
Tasks:  54 total,   3 running,  51 sleeping,   0 stopped,   0 zombie
Cpu(s):   6.3% user,   1.0% system,   0.0% nice,  92.7% idle
Mem:    450448k total,   293680k used,   156768k free,     6316k buffers
Swap:   971892k total,        0k used,   971892k free,   189764k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  619 root      16   0 97492  14m 2936 S  5.7  3.4   0:06.46 XFree86
  943 knoppix   10   0 15312  14m  13m R  0.7  3.4   0:00.51 kdeinit
 1050 knoppix   10   0 16844  16m 8236 S  0.7  3.7   0:01.82 gimp-2.0
  971 knoppix   10   0  1032 1032  840 R  0.3  0.2   0:00.28 top
    1 root       8   0    76   76   52 S  0.0  0.0   0:04.73 init
    2 root       9   0     0    0    0 S  0.0  0.0   0:00.02 keventd
    3 root      19  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd_CPU0
    4 root       9   0     0    0    0 S  0.0  0.0   0:00.00 kswapd
    5 root       9   0     0    0    0 S  0.0  0.0   0:00.00 bdflush
    6 root       9   0     0    0    0 S  0.0  0.0   0:00.00 kupdated
   12 root       9   0     0    0    0 S  0.0  0.0   0:00.00 khubd
   16 root       9   0     0    0    0 S  0.0  0.0   0:00.00 usb-storage-0
   17 root       9   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
  477 root       9   0   764  760  648 S  0.0  0.2   0:00.01 pump
  549 root       9   0   660  660  576 S  0.0  0.1   0:00.01 automount
  557 root       8   0  2536 2536 1212 S  0.0  0.6   0:00.14 bash
  558 root       8   0  2536 2536 1212 S  0.0  0.6   0:00.09 bash
``` See how a live CD with all those programs open is using only a little over half the RAM?

Okay, this is Ubuntu with nothing open but a terminal: ```
top - 21:34:01 up 11 min,  1 user,  load average: 0.55, 0.56, 0.38
Tasks:  73 total,   2 running,  71 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3% us,  0.0% sy,  0.0% ni, 99.7% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    451852k total,   338312k used,   113540k free,    16060k buffers
Swap:   971892k total,        0k used,   971892k free,   225920k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8321 root      16   0 87080  18m 2964 S  0.3  4.2   0:22.58 Xorg
    1 root      16   0  1564  524  460 S  0.0  0.1   0:00.91 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.03 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  110 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
  138 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  139 root      15   0     0    0    0 S  0.0  0.0   0:00.28 pdflush
  141 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  140 root      15   0     0    0    0 S  0.0  0.0   0:00.07 kswapd0
  726 root      15   0     0    0    0 S  0.0  0.0   0:00.01 kseriod
  907 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 2367 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2440 root      25   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 2441 root      15   0     0    0    0 S  0.0  0.0   0:00.43 usb-storage
 3973 root      15   0     0    0    0 S  0.0  0.0   0:00.31 kjournald
``` The RAM use is much higher. If I open up Firefox, JuK, and Thunderbird, it uses almost all the RAM and some swap.

What makes this crazier? I get the same RAM use in XFCE, KDE, and Gnome. It's always high... as long as it's Ubuntu.

So, any ideas? Why is it just Ubuntu and not Knoppix or Windows? Why is it all of a sudden doing this after nine months--even with no internet connection, even with a fresh reinstallation?

If this keeps up... I may have to switch to Knoppix or plain Debian. I don't mind using something light like XFCE (I kind of like it, actually), but XFCE's not making any difference, and it's getting to the point where I can't check email, use the internet, and listen to music at the same time--which is ridiculous with 512 MB of RAM.

---

### Post by Qrk on 2006-02-05
hmm... I never noticed it, but it seems I have the same problem.
```
01:42:15 up 17 min,  2 users,  load average: 0.23, 0.36, 0.33
Tasks:  89 total,   2 running,  87 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.3% us,  3.7% sy,  0.0% ni, 88.7% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:    451660k total,   427116k used,    24544k free,    19580k buffers
Swap:  1775172k total,    12532k used,  1762640k free,   187308k cached
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8231 root      15   0  101m  30m 8432 S  6.7  6.9   0:33.46 Xorg
 9488 daniel    15   0 31356  12m 8528 S  2.7  2.9   0:00.94 gnome-terminal
 8839 daniel    16   0  120m  42m  21m R  1.7  9.6   0:19.52 epiphany
 9440 daniel    16   0 57144 9568 7484 S  0.3  2.1   0:00.21 evolution-alarm
 9502 daniel    16   0  2132 1084  844 R  0.3  0.2   0:00.02 top
    1 root      16   0  1564  532  460 S  0.0  0.1   0:01.08 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    4 root      12  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  119 root      10  -5     0    0    0 S  0.0  0.0   0:00.21 kblockd/0
  145 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  146 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  148 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  147 root      15   0     0    0    0 S  0.0  0.0   0:00.41 kswapd0
  733 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod


```

It hasn't been that slow, but then again, I rarely multitask heavily.

---

### Post by Iandefor on 2006-02-05
[quote=aysiu]Okay, this is Ubuntu with nothing open but a terminal: ```
top - 21:34:01 up 11 min,  1 user,  load average: 0.55, 0.56, 0.38
Tasks:  73 total,   2 running,  71 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3% us,  0.0% sy,  0.0% ni, 99.7% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    451852k total,   338312k used,   113540k free,    16060k buffers
Swap:   971892k total,        0k used,   971892k free,   225920k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8321 root      16   0 87080  18m 2964 S  0.3  4.2   0:22.58 Xorg
    1 root      16   0  1564  524  460 S  0.0  0.1   0:00.91 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.03 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.13 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  110 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
  138 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  139 root      15   0     0    0    0 S  0.0  0.0   0:00.28 pdflush
  141 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  140 root      15   0     0    0    0 S  0.0  0.0   0:00.07 kswapd0
  726 root      15   0     0    0    0 S  0.0  0.0   0:00.01 kseriod
  907 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 2367 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2440 root      25   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 2441 root      15   0     0    0    0 S  0.0  0.0   0:00.43 usb-storage
 3973 root      15   0     0    0    0 S  0.0  0.0   0:00.31 kjournald
``` [/quote] 
Why are KDE processes running if you're using Ubuntu with GNOME? I'm actually just curious; I have no idea as to how to begin fixing your problem, unfortunately :(.

EDIT: Actually, I have one thought. Do you keep /home on a separate partition from your main Ubuntu installation?

---

### Post by r4ik on 2006-02-05
Here's my output i think there is  to many of mem used also this is on a Ubuntu only, aprox 1 month fresh installed.
Got 2 users can anybody highlite me on that please ?

top - 08:23:28 up  1:03,  2 users,  load average: 0.48, 0.37, 0.27
Tasks:  76 total,   2 running,  74 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.7% us,  1.5% sy,  0.0% ni, 89.0% id,  0.0% wa,  0.4% hi,  0.4% si
Mem:    516488k total,   507192k used,     9296k free,    83904k buffers
Swap:  1510068k total,        0k used,  1510068k free,   197804k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6908 root      15   0  158m  26m 7616 S  4.4  5.3   2:14.37 Xorg
 7650 r4ik      15   0 98.1m  34m  16m S  2.3  6.9   2:10.22 firefox-bin
 9244 r4ik      16   0 31996  13m 9068 R  2.1  2.7   0:04.46 gnome-terminal
 7569 r4ik      15   0 14200 8632 6640 S  0.9  1.7   0:17.33 metacity
 7582 r4ik      16   0 19440  10m 8200 S  0.2  2.1   0:05.58 wnck-applet
 7574 r4ik      16   0 22380  13m 9224 S  0.1  2.6   0:04.63 gnome-panel
 7576 r4ik      15   0 33656  19m  12m S  0.1  3.8   0:08.08 nautilus
 6430 hal       17   0  1864  632  544 S  0.0  0.1   0:01.41 hald-addon-stor
 7530 r4ik      15   0 20128 9652 6852 S  0.0  1.9   0:02.25 gnome-settings-
 7533 r4ik      15   0  2708 1436  888 S  0.0  0.3   0:00.76 gam_server
 7614 r4ik      15   0 21416  11m 8072 S  0.0  2.2   0:01.44 mixer_applet2
 7476 r4ik      16   0 18548 9580 7048 S  0.0  1.9   0:01.22 gnome-session
 7526 r4ik      16   0  6320 4820 1016 S  0.0  0.9   0:00.81 esd
 7545 r4ik      16   0  5928 2472 1832 S  0.0  0.5   0:00.57 xscreensaver
 7586 r4ik      15   0 18280 9732 7488 S  0.0  1.9   0:01.31 update-notifier
 7588 r4ik      16   0 19848 9392 7056 S  0.0  1.8   0:00.81 trashapplet
 7593 r4ik      15   0 37972 8720 6392 S  0.0  1.7   0:01.58 gnome-cups-icon

---

### Post by r4ik on 2006-02-05
I changed the kernel now notice the difference any change this might be a solution for you Aysiu ?

top - 09:36:05 up 15 min,  2 users,  load average: 0.10, 0.21, 0.20
Tasks:  76 total,   1 running,  75 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.5% us,  2.4% sy,  0.0% ni, 85.0% id,  0.0% wa,  0.7% hi,  0.4% si
Mem:    516488k total,   356048k used,   160440k free,    14008k buffers
Swap:  1510068k total,        0k used,  1510068k free,   208716k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7870 r4ik      15   0 31780  12m 8384 S  8.5  2.5   0:02.38 gnome-terminal
 6906 root      15   0  156m  24m 7184 S  5.0  4.8   0:33.34 Xorg
 7532 r4ik      16   0 20128 9656 6852 S  0.1  1.9   0:01.14 gnome-settings-
 7535 r4ik      15   0  2704 1428  888 S  0.1  0.3   0:00.29 gam_server
 7568 r4ik      16   0 14060 8324 6444 S  0.1  1.6   0:05.61 metacity
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.56 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 events/0
    4 root      13  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    5 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   72 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 kblockd/0
   98 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
   99 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush
  101 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  100 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  686 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod

---

### Post by GeneralZod on 2006-02-05
Are you suffering performance degradation at all? I see that you're not even touching swap.

It's odd that you claim to see it only in Ubuntu as *every* modern OS (Windows, OS X, Linux - all distros!) fills RAM up as much as is possible with cached files for efficiency purposes (RAM access is much, much faster than disk access).

A little more info here:

[http://ubuntuforums.org/showthread.php?t=125160&highlight=cache+ram](http://ubuntuforums.org/showthread.php?t=125160&highlight=cache+ram)

In short, this is expected and sufficient cached files will be instantly cleared as soon as an application requests more RAM.

Edit:

Ah, just checked out your second top output - where it said "nothing open but a terminal" I assumed you meant "nothing open but GNOME and gnome-terminal"! :) Yeah, that's pretty high, but again the vast majority of it is cached files.

Edit2:

Actually, re-reading your stuff, it does seem that something weird is going on, after all.  Ignore me :)

---

### Post by r4ik on 2006-02-05
The machine works perfect so no complaints there.
I posted the top output just because i was curious about it after Aysiu did.
So i learned something new today thanks for your reply.

---

### Post by aysiu on 2006-02-05
Thanks for the replies. Even if nothing fixes the problem, it's good to know I have community support.

In answer to people's questions:

1. I was running *top* in KDE at the time. In my original post I mentioned, though, that the same problem happens in XFCE and Gnome, too.

2. I could try a different kernel, but I didn't have any problems with this kernel until recently. So I should try the one with a 9 in it, instead of the one with a 10?

3. I've tried /home on a separate partition and on the / partition--no difference. Thanks for asking.

4. And, yes, it does affect performance (again, only recently--it was fine for nine months straight). I don't care if it *uses* a lot of memory, but if I can't do basic multi-tasking (three or four programs opening without slow-down), I may just have to switch over.

I'll see if there's other stuff that I can play around with to get it better. If I can't fix it, I'll probably install Debian and still just hang around these forums (what does Debian have--mailing lists?).

---

### Post by bartbes on 2006-02-05
I think he's actually meaning to upgrade your kernel to a 686 intead of 386 (if possible, Pentium 2 is sufficient) and a 64-bit use k7 (if you installed ubuntu 32-bit)

---

### Post by aysiu on 2006-02-05
[QUOTE=bartbes]I think he's actually meaning to upgrade your kernel to a 686 intead of 386 (if possible, Pentium 2 is sufficient) and a 64-bit use k7 (if you installed ubuntu 32-bit)[/QUOTE] How do I do that? Does it mean I have to recompile my kernel? Is that going to be a scary process (I've never done it before)?

I can tell you right now that 64-bit doesn't work on this computer.

---

### Post by bartbes on 2006-02-05
well it's just apt-get... I think you know how to see your kernel version, to be sure here it is: ```
uname -r
```
if you see 386 at the end and you have at least a Pentium 2, type in: ```
sudo apt-get install *kernel_version_without_386*-686 
```
remember to put -686 **directly** after the kernel version

example
```
 sudo apt-get install 2.6.12-10-**686** 
```
(in my case)

---

### Post by Lord Illidan on 2006-02-05
You could just do:

```
sudo apt-get install linux-686
``` 
Offhand, I am also wondering about this.

```
Tasks:  76 total,   3 running,  73 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.9% us,  1.4% sy,  0.0% ni, 83.2% id,  0.4% wa,  0.6% hi,  0.4% si
Mem:    516316k total,   456052k used,    60264k free,    23836k buffers
Swap:  1510068k total,    28612k used,  1481456k free,   223360k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
15275 illidan   15   0 95916  43m  26m S  8.4  8.6   6:47.73 amarokapp
15047 root      16   0 86068  49m 3096 R  4.8  9.7   5:09.05 Xorg
15331 illidan   15   0  126m  59m  20m S  1.3 11.8   4:39.43 firefox-bin
15570 illidan   17   0 32832  17m  14m R  0.7  3.5   0:03.63 konsole
15572 illidan   16   0  2140 1028  816 R  0.2  0.2   0:00.72 top
15182 illidan   16   0 35572  22m  16m S  0.1  4.4   0:35.25 kicker
    1 root      16   0  1560  516  452 S  0.0  0.1   0:01.37 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.61 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   76 root      10  -5     0    0    0 S  0.0  0.0   0:00.49 kblockd/0
  100 root      15   0     0    0    0 S  0.0  0.0   0:00.88 pdflush
  101 root      15   0     0    0    0 S  0.0  0.0   0:02.46 pdflush
  103 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  102 root      15   0     0    0    0 S  0.0  0.0   0:00.80 kswapd0
  688 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 2431 root      16   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 4102 root      10  -5     0    0    0 S  0.0  0.0   0:00.23 reiserfs/0
 4154 root      12  -4  1668  524  452 S  0.0  0.1   0:00.23 udevd
 5501 hplip     18   0  4556 1092  988 S  0.0  0.2   0:00.00 hpiod
 6251 root      19   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 6600 root      15   0     0    0    0 S  0.0  0.0   0:00.01 kgameportd
 8008 dhcp      16   0  2460 1020  740 S  0.0  0.2   0:00.00 dhclient3
 8310 root      16   0  1960  960  528 S  0.0  0.2   0:00.01 acpid
 8325 syslog    16   0  1884  748  628 S  0.0  0.1   0:00.10 syslogd
 8342 root      15   0  1564  364  300 S  0.0  0.1   0:00.07 dd
 8344 klog      15   0  2688  488  436 S  0.0  0.1   0:00.18 klogd
 8357 messageb  16   0  2148  992  892 S  0.0  0.2   0:00.31 dbus-daemon
 8370 hal       16   0  5132 2004 1412 S  0.0  0.4   0:01.05 hald
 8375 hal       18   0  1868  356  356 S  0.0  0.1   0:00.00 hald-addon-acpi
 8393 hal       16   0  1872  432  420 S  0.0  0.1   0:03.36 hald-addon-stor
 8395 hal       16   0  1868  436  420 S  0.0  0.1   0:02.03 hald-addon-stor
 8411 cupsys    16   0  6304 1396 1116 S  0.0  0.3   0:00.40 cupsd
 8673 root      16   0  5468 1168 1028 S  0.0  0.2   0:00.09 nmbd
 8675 root      18   0  7724  992  992 S  0.0  0.2   0:00.00 smbd
 8681 root      18   0  7724  992  992 S  0.0  0.2   0:00.00 smbd
 8682 slimp3    16   0 20216 2660 1644 S  0.0  0.5   0:02.08 slimp3
 8999 root      16   0  2712  764  652 S  0.0  0.1   0:00.04 kdm
 9052 root      16   0  1936  756  688 S  0.0  0.1   0:00.00 cron

``` 
Those are my processes. I am wondering why Xorg takes so much, when there is no animation, etc, on screen..Firefox and Amarok are known for being bloodsuckers, but I am surprised at Kicker and Konsole, considering that only 1 tab was open in the latter, with no activity going on except top.

Edit : aysiu can you run ```
free
``` in a terminal and show the results here? Also, have you run memtest86?

---

### Post by aysiu on 2006-02-06
Thanks for the suggestions.
I'll give them a shot and report back.

---

### Post by Jason_25 on 2006-02-06
Here is the real reason for your "high" memory use.

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by aysiu on 2006-02-06
I don't mind if the numbers are high. I *do* mind a lot if it affects performance--and that's exactly what's happening. I can't have three or more applications open without **significant slowdown**.

---

### Post by prizrak on 2006-02-06
[QUOTE=aysiu]How do I do that? Does it mean I have to recompile my kernel? Is that going to be a scary process (I've never done it before)?

I can tell you right now that 64-bit doesn't work on this computer.[/QUOTE]
Actually it's mad easy just do 
```
sudo apt-get linux-686
``` 
If your run a Pentium system
OR
```
sudo apt-get linux-k7
```
If you run AMD Athlon. 
After installing the kernel you will have a choice of your new and your old kernel in GRUB. Make sure your new kernel works and then set it as default (it it doesn't do that for you automatically). You are also free to get rid of your old kernel once your new one works although some people prefer having more than one installed just in case.
I also have the memory reported as full in top but only half full in system monitor. The display depends on caching, with cache shown your entire memory is full w/o it, the memory use is fairly small. The slowdown is what's really weird, have you installed non-repo stuff that might be leaking memory? Such as DC++ for Linux or something like that.

---

### Post by aysiu on 2006-02-06
Thanks prizrak.
I was worried I'd have to recompile my kernel (sounds scary).
I'm at work right now, but when I get home, I'll try that out. Thanks.

---

### Post by aysiu on 2006-02-06
[QUOTE=Lord Illidan]You could just do:

```
sudo apt-get install linux-686
``` [/quote] Well, I tried 686. It feels... better. Still, it's not the same performance I got out of Ubuntu for the last nine months. If I'm listening to music, it'll still have awkward pauses or skips when I click a link in Firefox (or Opera or Epiphany or any browser), and sometimes the mouse trails a bit when I'm moving it.

> 
Edit : aysiu can you run ```
free
``` in a terminal and show the results here? ```
free
             total       used       free     shared    buffers     cached
Mem:        451680     441256      10424          0      11344     213876
-/+ buffers/cache:     216036     235644
Swap:       971892          0     971892
``` This is with the 686 kernel. 

> Also, have you run memtest86? I haven't. What does it do?

Incidentally, I installed Mepis (which I haven't had for about ten months now) on another partition, it works just fine. If I can't lick this thing, I may stick with Mepis until Dapper comes out. I'll try that memtest thing if it actually *does* something to the memory (apart from just testing it).

---

### Post by newuser111 on 2006-02-06
try renicing xorg

sudo dpkg-reconfigure xserver-common

try a different nice level 0 is what is recommended, but try higher maybe 10?

---

### Post by aysiu on 2006-02-06
[QUOTE=newuser111]try renicing xorg

sudo dpkg-reconfigure xserver-common

try a different nice level 0 is what is recommended, but try higher maybe 10?[/QUOTE] Can you break this down for me a little? 

What's *renicing*? 

What's the xserver-common and how does that differ from xserver-xorg (something I do have experiencing reconfiguring)?

What are nice levels? What happens if I pick the wrong one?

---

### Post by newuser111 on 2006-02-06
nice level is a cpu priority level, a lot of people recommend changing it to fix audio skipping problems

running 
sudo dpkg-reconfigure xserver-common asks what level you want, 0 is supposed to be the default

that info is stored in /etc/X11/Xwrapper.config

---

### Post by byen on 2006-02-06
[QUOTE=aysiu]Thanks prizrak.
I was worried I'd have to recompile my kernel (sounds scary).
I'm at work right now, but when I get home, I'll try that out. Thanks.[/QUOTE]
aysiu. I may be a bit late on this..but if you are still looking for an easy way to install the right kernel for you.. you might want to try poofy's [how-to]("http://www.ubuntuforums.org/showthread.php?t=85917").  Im not sure if changing the kernel would help you solve the ram issue but when using the default 386  kernel...my AMD 2800+ cpu would go all the way upto 100% most of the time with only the browser and a media player open! So after looking round I changed to the k7 kernel (for AMD) and BAM! I saw a huge difference in cpu usage and the overall performance. Now, some people seem to have a noticable difference and some saw no change whatsoever....so I guess you have to try it out and see if changing the kernel helps your case.
Hope my post helps you in some way.
Goodluck!

---

### Post by newuser111 on 2006-02-06
i got the best speed increase from compiling my own kernel, really its not that hard

[http://www.ubuntuforums.org/showthread.php?t=84174&highlight=vanilla+kernel](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=vanilla+kernel)

but instead i used the archck patch instead of the ck patch

the howto needs a few improvements, i might write my own eventually

---

### Post by aysiu on 2006-02-07
Progress report:

1. I tried *memtest*. It seemed to have no problems, but the test just kept running on and on. After two hours, I said "screw it" and just reboot the computer.

2. The AMD kernel (k7) didn't really seem to make a difference.

3. Changing the "nice" value made applications load up and move faster, but the music still gets interrupted.

Thanks to everybody for trying to help me out. I really do appreciate it. I think I'll be doing a little bouncing back and forth between Ubuntu and Mepis until Dapper comes out.

**Edit**: I changed the "nice" value to -5 just to test it out. Then I changed it to -10, and it made a big difference. I had to have about six applications open to make the music player skip. We'll see how many Firefox tabs it takes otherwise. Thanks again to everyone for helping me out!

I was reading the description in the reconfigure of xserver-common, and it said for single-user environments, it's okay not to play "nice," but no one ever told me about this before this thread. I'm definitely a single user (my wife has her own computer), and it would have been nice to know I can make X the priority. Only question: if X is now the priority, what's getting the shaft? Anything?

---

### Post by RAOF on 2006-02-07
Have you tried sorting the top output by memory usage?  Do you have any idea what's sapping the memory?

Finally, have you tried killing the update-notifier (killall update-notifier)?  That seems to go crazy quite a lot, for some reason.

---

### Post by newuser111 on 2006-02-07
> 
Edit: I changed the "nice" value to -5 just to test it out. Then I changed it to -10, and it made a big difference. I had to have about six applications open to make the music player skip. We'll see how many Firefox tabs it takes otherwise. Thanks again to everyone for helping me out!

good experiment aysiu, you might be interested to know that -10 nice level for xorg was the default for debian until recently, thats why mepis and knoppix might be running better for you

i have my nice level set to 0 for xorg but what solved audio skipping for me was downloading and compiling the latest alsa from source

---

### Post by aysiu on 2006-02-07
Once again, I appreciate your help. Thank you.

Everything seems to be more or less back to normal (though, I'm still baffled as to how it got like that after nine months of no problems).

---

### Post by newuser111 on 2006-02-07
no problem, I have no clue what could cause a slowdown after so long, some say the ext3 filesystem gets slow and bloated after a while but that could just be nonsense talk, still one reason i want to try reiser4 when its released, looks like a very cool filesystem

---

### Post by aysiu on 2006-02-07
[QUOTE=newuser111]good experiment aysiu, you might be interested to know that -10 nice level for xorg was the default for debian until recently, thats why mepis and knoppix might be running better for you[/QUOTE] Actually, it still is for Mepis--I just double-checked!

---

### Post by aysiu on 2006-02-08
**New development**: so everything appears to be much better. Here's what's weird. If I run apt-get (from the command-line) or Synaptic Package Manager, then the audio skipping happens again--only using apt-get or Synaptic.

Other applications don't appear to be affecting sound any more. Is that weird?

---

### Post by Bartender on 2006-02-08
[QUOTE=aysiu]I tried *memtest*. It seemed to have no problems, but the test just kept running on and on. After two hours, I said "screw it" and just reboot the computer.[/QUOTE]
 Is the Ubuntu memtest any different from the memtest download that you install to a floppy?  I've used the downloaded version on several different Windows computers.  Pretty sure it'll continue looping thru the tests until hell freezes over.  As long as it doesn't start reporting errors you're good to go

---

### Post by aysiu on 2006-02-09
[QUOTE=Bartender]Is the Ubuntu memtest any different from the memtest download that you install to a floppy?  I've used the downloaded version on several different Windows computers.  Pretty sure it'll continue looping thru the tests until hell freezes over.  As long as it doesn't start reporting errors you're good to go[/QUOTE] Good to know. Last night I ran it overnight (for about eight hours), and there were no errors, so I guess the memory is good.

I did spend a bit of time playing around with Knoppix (hard drive install) and Mepis. They both had better responsiveness (and none of that audio problem), but they had other issues, and I ultimately ended up... missing Ubuntu (warts and all). There's something about Ubuntu--I don't know. Well, I'm going to tough it out... maybe see how Dapper does in a couple of months...

---

