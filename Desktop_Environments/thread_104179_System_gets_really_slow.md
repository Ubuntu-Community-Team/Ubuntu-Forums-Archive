---
title: "System gets really slow"
date: 2005-12-15
forum: Desktop Environments
---

### Post by christooss on 2005-12-15
Hello

I have problem :) When I boot in to ubuntu its fast. All applications start fast no problems. But when I have computer runing for about 12 hours (depends) how long i m away from home) I get mayor slow down.

How slow? So slow that If I have terminal in front of FF it takes 1 minute to show whole FF. I noticed that removing cache from FF speeds up a little. But not good enough. Argh.

The problem is that even though I clean cache in FF I cannot watch film. Processor is always on 100% :(

Do you have any ideas about that?

---

### Post by kingsidy on 2005-12-15
A memory leak is a possibility.

---

### Post by GeneralZod on 2005-12-15
[QUOTE=kingsidy]A memory leak is a possibility.[/QUOTE]

Especially if Firefox is involved. OP - how much RAM do you have? Next time it happens, can you post 

```
top
```

output?

---

### Post by christooss on 2005-12-15
I have 256 RAM. Yes it is memory leak is the cause of my problems. Look at the swap its used to :)

Im posting top beacause system is getting slow :( but I can still surf the net and watch movies :)
```
top - 22:50:57 up  5:15,  2 users,  load average: 1.16, 1.10, 1.05
Tasks:  74 total,   3 running,  71 sleeping,   0 stopped,   0 zombie
Cpu(s): 37.9% us,  7.5% sy,  0.0% ni, 50.7% id,  1.3% wa,  0.3% hi,  2.3% si
Mem:    256800k total,   248248k used,     8552k free,     2708k buffers
Swap:   208804k total,   183232k used,    25572k free,    55628k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
14701 matic     15   0 31668  13m 8400 S 14.1  5.2   0:01.74 gnome-terminal
 6892 matic     16   0 61016  31m 7284 R 13.8 12.5  38:28.81 amule
 6597 root      16   0  125m  20m 5492 R  8.2  8.0  18:12.45 Xorg
11515 matic     15   0 85856  14m 8028 S  7.9  5.6   9:06.44 bmpx
 6838 matic     15   0 45804  28m  848 S  0.7 11.3   0:47.02 gam_server
14719 matic     16   0  2132 1076  844 R  0.7  0.4   0:00.05 top
 6833 matic     15   0 20236 4228 3852 S  0.3  1.6   0:19.78 gnome-settings-
 6924 matic     15   0 21496 9084 6020 S  0.3  3.5   0:31.03 sensors-applet
 6981 matic     15   0 22316 5200 4416 S  0.3  2.0   0:31.08 clock-applet
    1 root      16   0  1560  468  444 S  0.0  0.2   0:01.55 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.26 events/0
    4 root      14  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   76 root      10  -5     0    0    0 S  0.0  0.0   0:00.15 kblockd/0
  107 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
```

But how can I "clear" ram and swap?

---

### Post by towsonu2003 on 2005-12-17
Did this get resolved? Also, does ```
sudo /etc/init.d/gdm restart
``` works? (Will restart X altoghether, save things before doing) That is, does memory goes back to normal after restarting X? I've been reading more and more threads about this, and I think it's happening to me too (but this is laptop and is up no more than 6 hours, so minor problem)...

---

### Post by christooss on 2005-12-18
Restarting x does speed system up. But not to much. When system is stalled I can wait 10 minutes to Xreboot. :(

But I really don't want to reboot :(

---

### Post by poptones on 2005-12-18
Do you use pan? I know that has some serious problems. Just leaving it open and idle can make the system prone to disk i/o flakiness.

You might also try putting "killall gam_server" on an hourly cron and see if that nails it down.

---

### Post by kosmic on 2005-12-18
To clean the Swapp do :
 
sudo swappoff
and then
sudo swappon
 
:) it's a bit radical, but you don't need to restart your system
 
ups sorry I forgot -> sudo swappoff /dev/YourSwappPartition
then again with swappon

---

### Post by sabitha on 2005-12-18
[QUOTE=kosmic]To clean the Swapp do :
 
sudo swappoff
and then
sudo swappon
 
:) it's a bit radical, but you don't need to restart your system
 
ups sorry I forgot -> sudo swappoff /dev/YourSwappPartition
then again with swappon[/QUOTE]
 
then how to know where is my swapPartition :(

---

### Post by kosmic on 2005-12-18
ok it's simple do this in a terminal :
 
sudo fdisk -l (it's a small L) and with should say, post the result where so I can point you in the right direction.
 
I'm not in my box :(

---

### Post by christooss on 2005-12-18
Its writen in fstab :)

What is gam_server for?

---

### Post by GeneralZod on 2005-12-18
[QUOTE=christooss]Its writen in fstab :)

What is gam_server for?[/QUOTE]

It's the successor to famd, the File Access Monitor Daemon.

---

### Post by sabitha on 2005-12-18
$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4834    38829073+  83  Linux
/dev/hda2            4835        4998     1317330    5  Extended
/dev/hda5            4835        4998     1317298+  82  Linux swap / Solaris

---

### Post by kosmic on 2005-12-18
Ok. thank you **sabitha**
 
The swapp partition is always the one that says in the end ->Linux swap / Solaris, or it was the numerial value of 82, so in your case is partition : /dev/hda5

---

### Post by sabitha on 2005-12-18
thanks kosmic ;)

---

### Post by christooss on 2005-12-18
[QUOTE=poptones]Do you use pan? I know that has some serious problems. Just leaving it open and idle can make the system prone to disk i/o flakiness.
[/QUOTE]

WHat is pan?

---

### Post by poptones on 2005-12-18
pan is a gnome usenet client. If you have to ask, you're probly not using it.

gam_server can cause memory leaks and other flakiness. Killing it only results in the resources being freed and it restarting. if that's the culprit, killing it every hour should result in you not having to reboot. Do you know how to set a cron task?

---

### Post by christooss on 2005-12-18
Hm I set up a cron tab with

1 * * * * killall gam_server

Is that right thing to do?

---

### Post by christooss on 2005-12-18
I think killing gam_server does the shit :)

Thank you very much

---

### Post by towsonu2003 on 2005-12-20
[QUOTE=christooss]Hm I set up a cron tab with

1 * * * * killall gam_server

Is that right thing to do?[/QUOTE]

I don't have my linux book with me but, doesn't that kill the poor thing every 1 minute?

---

### Post by Gurgeh on 2005-12-20
God damn I love this shit, U can even get it to flush its own cache? ts almost too much to ask!

---

### Post by christooss on 2005-12-20
[QUOTE=towsonu2003]I don't have my linux book with me but, doesn't that kill the poor thing every 1 minute?[/QUOTE]

Nope It kills this poor thing every first minute of an hour i.e. 16:01

I think :)

---

### Post by towsonu2003 on 2005-12-20
[QUOTE=christooss]Nope It kills this poor thing every first minute of an hour i.e. 16:01

I think :)[/QUOTE]
oops :) yes - p.159 of 'linux pocket guide' (I was serious about my linux book heheh)

poor thing...

---

