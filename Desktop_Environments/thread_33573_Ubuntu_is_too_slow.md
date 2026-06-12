---
title: "Ubuntu is too slow"
date: 2005-05-11
forum: Desktop Environments
---

### Post by Dax0r on 2005-05-11
I'm using Ubuntu hoary 5.04 and I think that's too slow...OpenOffice take 30 seconds to start,Firefox take 11 seconds (and hog my cpu when load a tab) and gnome-terminal 3 seconds...
The Dma is enabled ,I've a p4 2.5 Gh with 256 mb ram

---

### Post by blueplazma on 2005-05-11
Given your CPU, I bet that your problem is RAM.  From a terminal, run top and check how much free memory you have.

---

### Post by alastair on 2005-05-11
I'm not sure the reported times are /so/ bad. OO /is/ slow to load - try abiword/gnumeric etc.

I find it hard to believe that 256 MB RAM is not enough to run a Gnome desktop though.

I'd check disk speed as well i.e.

hdparm -tT <partition>

---

### Post by rosslaird on 2005-05-11
OpenOffice is horribly slow no matter what system you have.
And yes, believe it or not, Gnome is a bit slow on 256M of RAM.
Firefox is also a bit sluggish.

Xfce is much faster overall than gnome (I think I saw stats around here the other day that had gnome at 300 megs and xfce at 80). And, there are several faster options for your other tasks:

Kazehakase is a very fast (and very cool) browser.
Galeon is also faster than Firefox.
AbiWord is much faster than OO.
The xfce terminal is quite peppy.

Ross

---

### Post by az on 2005-05-11
I am running a processor one-third the speed of yours and Open office takes about 25 seconds to load.  Firefox takes five.  There is something wrong here...

---

### Post by AsteriskNix on 2005-05-11
Try installing and running Prelink before you give up on Ubuntu.

there are a few stickies running around here but the command after you download it from Universe is 

sudo prelink -amvR

This basically caches all the binaries and speeds things up dramatically.

---

### Post by dewey on 2005-05-11
Try prelinking, dma mode, or installing another kernel (k7, 686)

Also, try XFCE, it's much more lightweight.  It looks like ram is your problem, 256 is low, and I'm guessing it's a slower speed, maybe 2100 DDR.

---

### Post by bcrowell on 2005-05-11
[QUOTE=Dax0r]I'm using Ubuntu hoary 5.04 and I think that's too slow...OpenOffice take 30 seconds to start,Firefox take 11 seconds (and hog my cpu when load a tab) and gnome-terminal 3 seconds...
The Dma is enabled ,I've a p4 2.5 Gh with 256 mb ram[/QUOTE]

A lot of the software you're talking about just *is* slow (OOo and Gnome). You might want to try aterm instead of gnome-terminal. OTOH, 11 seconds for Firefox is definitely way too slow -- I have a plain Debian machine with similar specs, and it takes less than 2 seconds.

---

### Post by TheCondor on 2005-05-12
I also have a small 'issue' with firefox, that is, when no other instance of firefox is running, it takes too long to open. While everything else starts up very quickly, firefox ( and mozilla too ) seem to want to start slow. I have enabled prelinking and all other goodies but it happened from day one, with warty and hoary too. My system is a p4 2.6ghz with 1.5gb ram. I dont mind because my pc runs all the time and Im just stating this as a fact on my pc, neither do I mind about it, cos Firefox is always running with tabbed browsing ( so I dont have 1209393 instances of it in my taskbar ) and everything else works like a charm. ( uptimes are so smooth too, the system works generally better than my windows xp one, given the same days of uptime and -ab-use )

---

### Post by picturesqueweb on 2005-05-12
I have even less memory that you and am very pleased with performance. I take into consideration what I have and set realistic expectations. I've also followed the advice given in this topic and in others. It takes time to tweak the system to get things to work satisfactorily. Reading the forums and experimenting is a must.

Thanks rosslaird for some great program recommendations!

---

