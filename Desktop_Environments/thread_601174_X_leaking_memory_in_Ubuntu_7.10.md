---
title: "X leaking memory in Ubuntu 7.10?"
date: 2007-11-03
forum: Desktop Environments
---

### Post by almkglor on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/151168](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/151168) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello all,

Although the "related" bug here is for Nvidia, I'm using Intel, and it also appears to have an X memory leak WITHOUT Compiz.

I upgraded from 7.04 to 7.10 almost as soon as it was available; this laptop originally had 6.06LTS installed, and then upgraded to 6.10 and then 7.04, and now has 7.10.  No, I'm too lazy to do a clean install, and really what's the point of supporting an internet-based upgrade if I have to clean install anyway.

It seems that my X server keeps growing in memory.  At X server reset it starts at only 1% memory used, an then keeps growing.  After about a day it's so unbearably slow with >60% memory, and Linux keeps thrashing swap to and from disk.

The problem was even worse when I first installed with Compiz - there it took only about an hour to reach thrashing mode.  I have since removed Compiz, but the problem remains, it just takes longer to appear.

My computer is a laptop built around Intel945GM integrated board, and the current screen driver is "intel - Experimental modesetting driver for I..." (the I... is cut because it doesn't display the driver name completely on the Screen and Graphics screen).

```
top - 11:53:37 up 1 day,  3:38,  3 users,  load average: 0.05, 0.12, 0.15
Tasks: 128 total,   2 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.5%us,  0.2%sy,  0.0%ni, 97.2%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1019888k total,   952912k used,    66976k free,     9012k buffers
Swap:        0k total,        0k used,        0k free,   196816k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
10201 root      15   0  760m 364m 9084 S    0 36.6   6:01.91 Xorg               
13764 almkglor  15   0  541m  87m  23m S    3  8.7   0:28.86 firefox-bin        
13792 root      15   0  195m  32m  11m S    0  3.3   0:01.77 displayconfig-g    
10371 almkglor  15   0  393m  26m  14m S    0  2.6   0:02.52 nautilus           
10369 almkglor  15   0  281m  22m  13m S    0  2.2   1:06.74 gnome-panel        
10469 almkglor  15   0  227m  20m  11m S    1  2.1   0:02.68 gnome-terminal     
10448 almkglor  15   0  215m  15m  10m S    0  1.6   0:00.31 mixer_applet2      
10397 almkglor  15   0  173m  15m 7712 S    0  1.6   0:00.18 python             
10383 almkglor  15   0  210m  14m  10m S    0  1.5   0:00.28 update-notifier    
10367 almkglor  15   0  115m  12m 8252 S    0  1.3   1:26.54 metacity           
13791 almkglor  16   0  143m  12m 8456 S    0  1.3   0:00.45 gksu               
10361 almkglor  15   0  219m  12m 8696 S    0  1.2   0:06.72 gnome-settings-    
12593 almkglor  15   0  135m  11m 7744 S    0  1.2   0:02.23 notification-da    
10400 almkglor  15   0  192m  11m 9036 S    0  1.2   0:00.28 nm-applet          
10418 almkglor  15   0  286m  10m 7996 S    0  1.0   0:00.08 trashapplet        
10408 almkglor  15   0  209m 9396 6060 S    0  0.9   0:00.14 gnome-power-man    
10300 almkglor  15   0  179m 8732 6924 S    0  0.9   0:00.10 x-session-manag    

```

It gets even worse when playing NetHack on a GUI interface - the GUI keeps opening windows, and it seems that the opening and closing of the windows makes it consume memory faster.  As everyone knows, NetHack makes use of all the latest graphics enhancements, though, so I guess it's just expected that an 64-bit microprocessor can't cope with it.

---

### Post by jtgalway on 2007-11-21
Having same problem with Gutsy using Intel graphics. I upgraded from Feisty a few weeks ago and since then I get Xorg absorbing vast swathes of memory when I leave the computer running for any length of time. Must be a memory leak - something's not getting freed properly.

When I restart everything goes back to "normal". Xorg uses something like ~200MB. Then after a while (a couple of days, say) it slowly rises up to it's current state (~900MB). Everything starts to slow down and things don't refresh well.

I'm using a Dell Optiplex GX270 with 1GB of RAM and 2GB swap on an 80GB harddrive. Graphics are integrated Intel ones (i810 I think).

Is there a workaround/fix for this? I see it listed on a few other posts and for different/earlier versions.

---

### Post by Dr. Cox on 2007-11-21
hi there,

same prob here, i think. i'm running an acer travelmate 290 with intel-chipset, centrino 1,4 and 512 ram. it only recently started, that gutsy freezes on me.  i can't even log out with cntr-alt-backspace.

i'd like to help and share experience. 

how can i get the nice command line output of my processes that you used above. (i only use the gui in gnome.... sad, i k now.)

---

### Post by Linteg on 2007-11-21
[QUOTE=Dr. Cox]
how can i get the nice command line output of my processes that you used above. [/QUOTE]
Start your preferred terminal and run *top*, and when you want it to go away, press q to quit.

---

### Post by jtgalway on 2007-11-22
I must note also that I am using Gnome. I have seen a few posts where people are using KDE and seeing similar problems, so it's not restricted to one desktop environment, or even version. I see similar problems in posts back to Dapper and Edgy. 

Does anyone know if there's a bug logged for this? I don't know much about the rules governing bug logging, but it might be worthwhile if it's as widespread as the boards might lead one to believe. I'm not running anything heavy like games or anything - just Firefox and  emacs, terminals etc for programming.


Current Xorg usage: 960MB!!!

```
top - 09:33:36 up 6 days, 22:45,  4 users,  load average: 0.63, 0.65, 0.60
Tasks: 120 total,   3 running, 113 sleeping,   4 stopped,   0 zombie
Cpu(s): 18.3%us,  4.0%sy,  0.0%ni, 77.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026992k total,   967172k used,    59820k free,    41136k buffers
Swap:  3004112k total,   681432k used,  2322680k free,    85564k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                        
 4554 root      15   0  958m 417m 6048 S 11.0 41.6 110:50.48 Xorg                                                           
 9221 ----      16   0  466m 247m  27m R  7.0 24.7 373:21.85 firefox-bin                                                    

```

---

### Post by featherbottoms on 2007-11-23
I'm having a similar problem.  I'm running KDE with Ubuntu 7.10, gutsy and a dual head matrox video card.  My memory right now shows 1,004,456 kb used and 31,156 free (I had 18,000 free when we came in this morning).  This is what my terminal showed a little while ago:
```

Tasks: 119 total,   6 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.3%us,  2.0%sy,  0.0%ni, 79.1%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035612k total,   973540k used,    62072k free,    23184k buffers
Swap:  1630556k total,    34784k used,  1595772k free,   256688k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4810 root      15   0  420m 347m 5356 S  8.3 34.4  52:46.03 Xorg
10223 debora    15   0  285m 165m  29m R  8.3 16.3  47:25.50 firefox-bin

```

I keep having to reboot my machine just to keep it running during the day.  I'm not the computer person in the family so I hope someone has told the folks that can fix this that it's a problem.  I believe I'm about to drive my husband crazy complaining about this to him.

featherbottoms

---

### Post by jtgalway on 2007-11-26
Hey there,

I just checked out my firefox version and upgraded it (via Synaptic) to version firefox3-0 instead of the regular firefox package. For now at least, this seems to be helping. My current Xorg usage is something like 340MB. I had let things run as they were a few days ago and it just crunched my system after using more than 1.2GB!!!

I found this morning that firefox was just really sluggish and the whole system was slow. It was using >80% CPU capacity for no good reason, so I killed it and upgraded. Now everything seems to be tickety-boo. We'll see if it holds up.

---

### Post by MarinaraOfDeath on 2007-11-26
> **almkglor said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/151168](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/151168) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello all,

Although the "related" bug here is for Nvidia, I'm using Intel, and it also appears to have an X memory leak WITHOUT Compiz.

It seems that my X server keeps growing in memory.  At X server reset it starts at only 1% memory used, an then keeps growing.  After about a day it's so unbearably slow with >60% memory, and Linux keeps thrashing swap to and from disk.

The problem was even worse when I first installed with Compiz - there it took only about an hour to reach thrashing mode.  I have since removed Compiz, but the problem remains, it just takes longer to appear.

My computer is a laptop built around Intel945GM integrated board, and the current screen driver is "intel - Experimental modesetting driver for I..." (the I... is cut because it doesn't display the driver name completely on the Screen and Graphics screen).

...

It gets even worse when playing NetHack on a GUI interface - the GUI keeps opening windows, and it seems that the opening and closing of the windows makes it consume memory faster.  As everyone knows, NetHack makes use of all the latest graphics enhancements, though, so I guess it's just expected that an 64-bit microprocessor can't cope with it.

1) Good point about NetHack :grin:

2) This sounds an awful lot like [what I've been seeing]("http://ubuntuforums.org/showthread.php?t=597792"). Compiz just makes the hanging happen faster, but it happens with metacity too. Last night, when it happened again, I did sudo killall gnome-panel (had to do it twice) since top told me that was the problem, and then within 15 minutes is happened yet again, with some other program (I think it was X, but I'm not sure, so I'll pay better attention the next time it happens). 

Scanning the forums, it looks like there's some underlying problem that people are seeing as massive amounts of memory and cpu being soaked up by something, causing some program to become essentially frozen for long periods of time. Kind sad, even though it was getting long in the tooth, and I really love a lot of the improvements in Gutsy, Dapper was fundamentally more stable than Gutsy for day-to-day work. I hope we all can dig up enough info that the pattern can be deciphered and this problem fixed in a future release.

---

### Post by snakep on 2007-11-27
I am getting memory problems as well, but Xorg doesn't seem to be the biggest culprit.  I am running the 64-bit version, so at first I thought that might be related to the problem, but it looks like most people are using 32-bit.  I noticed the problem last night when trying to run gmsh, and I kept getting "Ran out of GART memory" and "Error: Could not get dma buffer... exiting".  

Here's the output of top:

```
top - 08:33:03 up 45 min,  3 users,  load average: 0.42, 0.18, 0.17
Tasks: 111 total,   3 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6%us,  5.6%sy,  0.0%ni, 86.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1029484k total,  1018096k used,    11388k free,   152392k buffers
Swap:  1461872k total,        0k used,  1461872k free,   489156k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5766 jjhall    15   0  550m  92m  24m S  0.3  9.2   1:29.12 firefox-bin        
 5238 root      15   0  422m  82m 7752 S 11.9  8.2   1:34.03 Xorg               
 5803 jjhall    15   0  267m  28m  13m R  0.7  2.8   0:02.21 gnome-terminal     
 5471 jjhall    15   0  336m  20m  14m S  0.0  2.1   0:00.62 nautilus           
 5468 jjhall    15   0  281m  20m  13m S  0.0  2.0   0:02.81 gnome-panel        
 5617 jjhall    15   0  190m  19m 7688 S  0.0  1.9   0:03.46 compiz.real        
 5705 jjhall    15   0  173m  15m 7716 S  0.0  1.5   0:00.16 python             
 5739 jjhall    15   0  219m  15m  10m S  0.0  1.5   0:00.13 mixer_applet2      
 5641 jjhall    15   0  201m  13m 9792 S  0.0  1.4   0:00.13 update-notifier    
 5736 jjhall    15   0  203m  13m 9540 S  0.0  1.3   0:00.08 fast-user-switc    
 5692 jjhall    15   0  199m  13m  10m S  0.0  1.3   0:00.13 nm-applet          
 5459 jjhall    15   0  219m  12m 8688 S  0.0  1.2   0:00.67 gnome-settings-    
 5659 jjhall    15   0  239m  11m 9072 S  0.0  1.1   0:00.04 evolution-alarm    
 5658 jjhall    15   0  227m  10m 7952 S  0.0  1.0   0:00.12 trashapplet        
 5616 jjhall    15   0  124m   9m 7484 S  0.0  1.0   0:02.06 gtk-window-deco    
 5681 jjhall    34  19 69132 9.9m 2708 R  0.0  1.0   0:03.57 trackerd           
 
```

Here's the output of free -m:

```
Aragorn:~/Documents/research> free
             total       used       free     shared    buffers     cached
Mem:          1005        994         11          0        148        477
-/+ buffers/cache:        367        637
Swap:         1427          0       1427

```

It hasn't used swap very much, but there is a lot of memory in cache.  I know firefox isn't hogging it, because it's limited to 50 MB of cache.  Unfortunately, I'm not really sure what all of the output from free means.  Could someone explain?

---

