---
title: "High CPU usage in Compiz in LTS 12.04"
date: 2012-04-30
forum: Desktop Environments
---

### Post by beboylips on 2012-04-30
Hello Community,

I am running Ubuntu 12.04 64-bit on my desktop at home. It has the following specs:

I5-2500k
AMD ATI HD 6850 1 GB PCIe x16 (using the closed-source drivers from ATI, FGLRX )
ASRock Pro3 Gen3

linux 3.2.0-28
Using ubiquity 3D environment

When playing videos in Totem or VLC, the compiz cpu is pretty high (around 80% CPU usage for compiz for one core).

If anyone has any advice, please share :)

Thank you in advance!

-Beboy

---

### Post by zombifier25 on 2012-04-30
Compiz is a 3D compositing windows manager, so expect it to use quite an amount of CPU, especially when doing heavy tasks.
Other than that, I'm blind as a bat when it comes to hardware :P

---

### Post by beboylips on 2012-04-30
Anybody thinks its a software bug or an issue with the ATI driver? Anyone else having the same problem?

-Beboy

---

### Post by QIII on 2012-04-30
What is your CPU usage at idle?

When you have totem or VLC open without running a video?

---

### Post by mwolfe on 2012-05-01
I am having this same issue. I have the indicator for system usage and althought it doesn't show much going on for cpu the system load is extremely high (greather than 1.0 most of the time).
Right now load just dropped a bit but here is what top says:

load average: 1.28, 1.06, 0.56

(I just rebooted after an xorg update to see if that fixed anything but it did not).


As far as cpu usage compiz typically uses 12-30% even when all I have running is a web browser like this (only 1 tab open) and top running in a terminal. 

Seems pretty high to me.. 

I was using the open source driver for about a week but found that my load average was pretty high on that (not as bad though) but much more annoying was that I constantly had to restart unity (unity --replace) because after sleep/wakeup would cause unity to be super slow and barely usable. Oddly sometimes the same issue would happen even when the system didn't go to sleep (maybe it was after it turned off the screens but didnt actually suspend but not sure).

I have a radeon 5770 and a 1st gen i7 processor, with 12gb of ram.. Other than these issues 12.04 has been great.

Also note that even with these issues my performance seems pretty good (well, with the properietary driver -- the open source driver performance was spotty).

---

### Post by mwolfe on 2012-05-01
After doing some more research it appears that a load of 1.0-2.0 isn't that high. Also I noticed if I use firefox instead of chrome my load average seems to be quite a bit lower (hovering more around 0.8 now and music is playing in one tab with like 6 tabs open total)... I thought over 1 was high because the graph showed really high in the indicator and also with my old computer I remember when the load was above 1.0 it was super slow. However that computer had only 2 cores with no hyperthreading. Now with this cpu I've got 4 cores and 8 total with hyperthreading, which means the load calculation is on a scale that goes to 8.0 which. I tested by opening a bunch of videos and running some recursive greps at the same time and found my load actually can get quite close to 8 if I work it hard enough (yet it was still slightly responsive even around 7).


Here is a good article that details what system load means and how it is calculated: [http://www.linuxjournal.com/article/9001?page=0](http://www.linuxjournal.com/article/9001?page=0)

---

### Post by gordintoronto on 2012-05-01
If you open a terminal and enter the command: top
you should get more accurate/lower readings than from system monitor.

---

### Post by mwolfe on 2012-05-01
I was using top as well as looking at the indicator. I am just saying that the load average has a poorly chosen scale considering it really goes up to 8 on my system but the scale only goes to about 1 it looks like.. Thus it looks like my system is overloaded when its only 1/8th in use.

As for cp usage, top shows
```
 
top - 14:38:46 up  3:26,  2 users,  load average: 1.25, 0.96, 0.90
Tasks: 238 total,   3 running, 234 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.5%us,  3.9%sy,  0.0%ni, 92.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  12265252k total,  8486772k used,  3778480k free,  1663368k buffers
Swap:        0k total,        0k used,        0k free,  4243512k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6749 mwolfe    20   0 1526m 106m  48m R   37  0.9  16:12.84 compiz             
 4191 mwolfe    20   0  641m  93m  25m S    5  0.8   7:24.77 plugin-containe 
```

---

### Post by beboylips on 2012-05-08
On idle, compiz is around 1-2, using $top.

---

### Post by ham_hal on 2013-01-06
Hi all,  I had also a high cpu usage with compiz and Ubuntu Pangolin. I use a laptop and the battery was being drained with this.  Using "top" I realized that the system monitor was also high. Changing the refresh rate fom 500 mS to 10 Seconds I saw that  the CPU usage in Compiz AND in the system monitor droped drastically.   I have removed the system monitor and use "top" when I'm curious about something. I liked having that "widget" in the top bar but not at that CPU-Usage.   I hope that this fix is also useful to someone else.

---

