---
title: "very(!) slow on hp-nx6125"
date: 2005-11-17
forum: Desktop Environments
---

### Post by jaykaycgn on 2005-11-17
hi

i just installed ubuntu 5.10 on my nx6125
3100+ sempron
512megs ram
7gb /, 600mb swap hd
ati mobility x300

at first i had problems with my graphics card but they seemd to be fixed now by installing fglrx drivers.
but now i notice that gnome is so slow that i can't work with it. opening eg. firefox takes over one minute, same for network-configuration tool and everything else. 

sudo hdparm -tT /dev/hda in genome says:

time cached reads: 68mb in 2.11 seconds = 32.20MB/sec 
time bufferd disk reads: 20mb in 3.26 seconds = 6.13Mb/sec

i think this is too slow!

hdparm at tty1 says similar poor mb/sec, ~50megs/s, ~17megs/s

i copied 60mb from my usb-storage in gnome in 40(!)minutes and the same file in tty1 in about 1 minute... whats wrong here??

dma for my hda is on!

please help me!! :confused: 

mike


/edit: i just added the systemload-applett which says that there is 60% cpu-load and when i just do anything it goes up to 100%. but under processes it shows me that about 40%cpu go to "gnome-system-monitor", the prog itself...?! when i close it the applet still shows about 60% load, but on the graph with a dark-blue curve. the light-blue one is nearly gone then.

lol sorry for my eng. ;-)


/edit2:
i figured that this strange load-thing is becauase the processor spends nearly 50% time on IOWait! why is that??

---

### Post by jackqu7 on 2005-11-19
I had the same problem with this laptop and fixed it thanks to this topic: [http://ubuntuforums.org/showthread.php?t=53094&highlight=nx6125]("http://ubuntuforums.org/showthread.php?t=53094&highlight=nx6125")

---

