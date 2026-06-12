---
title: "Whos good at this!! =]"
date: 2009-02-12
forum: General Help
---

### Post by Meohme3 on 2009-02-12
Here is the dilemma; firefox closes (crashes) when I use basic java and adobe  programs on the Internet. Here are the following sites I've been to then firefox crashes: Youtube (when I try to watch videos), Runescape (everything about the site), and my MySpace home page or anybody else's profile. I have all the latest java and adobe programs I believe so there shouldent be any problems there.

---

### Post by Meohme3 on 2009-02-12
Bump:lolflag:

---

### Post by AliTabuger7 on 2009-02-12
If the OS listed to the left of your post is any indication, you probably aren't using anywhere near the _latest_ versions of anything. 6.06 is still a supported release though.

It would be much more helpful if you could give some output by runnning firefox through the terminal until it crashes, then pasting the stuff from the terminal here. If i had to guess though, it might be a lack of powerful hardware. Given that you're using xubuntu, you are probably using a low end system. Java and Flash are resourse intensive, so you might be running out of some kind of resourse like CPU or RAM. Perhaps you should tell us your system specs too, by looking at the "system" tab of gnome-system-monitor.

---

### Post by Meohme3 on 2009-02-12
Maybe it will help if I post the results of top as firefox is crashing.

---

### Post by Meohme3 on 2009-02-12
alright whenever firefox crashes either it will say firefox or "abort" is taking up too much cpu's and memory.

I have like 256 RAM or somewhere around that area, I understand this is enough to get a better version but... I don't have the patience to go through how many steps there are.

---

### Post by Meohme3 on 2009-02-13
Bump:lolflag:

---

### Post by Slim Odds on 2009-02-13
As AliTabuger7 mentioned, run it from a terminal and see that it outputs.

Also, upgrade to 8.04.2

---

### Post by Meohme3 on 2009-02-13
Here are the results of top:


[CENTER]top - 17:39:19 up 1:20, 2 users, load average: 0.36, 0.75, 0.58
Tasks: 69 total, 3 running, 65 sleeping, 0 stopped, 1 zombie
Cpu(s): 14.0%us, 1.3%sy, 0.0%ni, 84.0%id, 0.0%wa, 0.3%hi, 0.3%si, 0.0%st
Mem: 255024k total, 161100k used, 93924k free, 2568k buffers
Swap: 433712k total, 17612k used, 416100k free, 51900k cached

PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
3812 root 15 0 106m 23m 6712 R 7.6 9.2 5:54.48 Xorg
4549 matt 15 0 45280 13m 8340 R 7.6 5.3 0:02.67 xfce4-terminal
4610 matt 15 0 2248 1100 844 R 0.3 0.4 0:00.08 top
1 root 16 0 1628 540 448 S 0.0 0.2 0:01.87 init
2 root RT 0 0 0 0 S 0.0 0.0 0:00.00 migration/0
3 root 34 19 0 0 0 S 0.0 0.0 0:00.00 ksoftirqd/0
4 root RT 0 0 0 0 S 0.0 0.0 0:00.00 watchdog/0
5 root 10 -5 0 0 0 S 0.0 0.0 0:00.06 events/0
6 root 10 -5 0 0 0 S 0.0 0.0 0:00.04 khelper
7 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kthread
9 root 10 -5 0 0 0 S 0.0 0.0 0:00.01 kblockd/0
10 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpid
11 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 kacpi_notify
73 root 10 -5 0 0 0 S 0.0 0.0 0:00.00 kseriod
105 root 16 0 0 0 0 S 0.0 0.0 0:00.03 pdflush
106 root 15 0 0 0 0 S 0.0 0.0 0:00.27 kswapd0
107 root 20 -5 0 0 0 S 0.0 0.0 0:00.00 aio/0[/CENTER]

---

### Post by Slim Odds on 2009-02-13
Dude, you're not listening.....

run firefox from a terminal and see what gets output when it crashes

---

### Post by Atzu on 2009-02-13
They are telling you to open a terminal and type in there: firefox and then go to the page that crash you and you will get an output, paste that output here.

---

