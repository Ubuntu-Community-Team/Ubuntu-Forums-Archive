---
title: "Strange hangs in Ubuntu 11.10"
date: 2012-01-14
forum: Desktop Environments
---

### Post by lz1dsb on 2012-01-14
So let me explain a little bit about my setup. 
I upgraded recently from 9.10 to 11.10. It was a clean install, I didn't use the upgrade option because I was quite at the end of the release cycle anyway :)
So far the system works fine (Dell Studion 1555 with Broadcomm networking chips) but I noticed the following strange issue which happens sporadically.
So, here's the problem. Sometimes the system would hang, but in a strange way. Why in a strange way? Because the keyboard and the mouse are still active, the programs are still running, but the Unity panel for example doesn't show when I have a program window maximized. When I close all windows though, the Unity panel appears and I can still use it and start applications. But not everything. Some applications wouldn't start at all from the Unity panel. Also sometimes the Dashboard wouldn't open. Also the work space switcher in Unity wouldn't work. After reboot everything works fine. Anybody else having similar experiences?
At first I thought that this was caused by Skype as it happened couple of times when I started it. But than it also happened a few times while Skype wasn't running at all...

---

### Post by lz1dsb on 2012-01-16
Am I the only one that has experienced this ;))) Wow... interesting..

---

### Post by Frogs Hair on 2012-01-16
The the panel in Unity 3D has hide settings and it will hide when  an application is maximized . If using Unity 3D , meaning you are selecting Ubuntu during login and have the CCSM installed you can change these settings.

I don't what is causing the system lag if you have installed a a recommended proprietary driver from additional drivers .

The launcher settings can be changed in the Unity plug-in inside CCSM . If you are experiencing lag while running Unity 2D I don't know what the problem may be . Posting more information about your computer such as memory , CPU , and graphics card may be useful  .

---

### Post by lz1dsb on 2012-01-16
I'll give it a try. I haven't messed around with the Unity configs so far. I have CCSM installed though. 
Regarding the specs:
It's a Dell Studio 1555 with 4GB RAM, the video card is ATI Mobilty Radeon HD 4570 and the CPU is Core 2 Duo T6500 2.1 GHz. I guess it should be enough for the Unity 3D which I'm using. (I recently checked on that as both Unity and Unity2D look quite similar... But for sure I'm running the 3D variant)

BTW what theme do you use. It's quite sleek! :)) In my old 9.10 installation I used an Apple like theme which was great. The one you use reminds me of it.


Regards,
Boyan

---

### Post by lz1dsb on 2012-01-18
I just checked it. On my system I use exactly the same config like in the snapshot you've posted.
How can I further troubleshoot this. It's quite annoying. 
Recently after two more such hangs my keyboard was also blocked...
Anyone?

---

### Post by bogan on 2012-01-18
Hi!,** lz1dsb**,
Have you checked if all the Unity Plugins are present and activated?
```
sudo ps ax | grep unity 
```Mine shows:```
alan-MS-7616:/# ps ax | grep unity
 2109 ?        S      0:00 /usr/bin/unity-window-decorator
 2114 ?        Sl     0:00 /usr/lib/unity/unity-panel-service
 2177 ?        Sl     0:00 /usr/lib/unity-lens-applications/unity-applications-daemon
 2179 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-music-daemon
 2181 ?        Sl     0:00 /usr/lib/unity-lens-files/unity-files-daemon
 2212 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
 2265 pts/0    S+     0:00 grep --color=auto unity
alan-MS-7616:/# 
```Chao!, **bogan**.

---

### Post by lz1dsb on 2012-01-18
Hi, 
Here's what this command shows on my machine:
```
bsotirov@bsotirov-Studio-1555:~$ sudo ps ax | grep unity
 2061 ?        S      0:02 /usr/bin/unity-window-decorator
 2071 ?        Sl     2:54 /usr/lib/unity/unity-panel-service
 2337 ?        Sl     0:00 /usr/lib/unity-lens-applications/unity-applications-daemon
 2339 ?        Sl     0:00 /usr/lib/unity-lens-files/unity-files-daemon
 2341 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-music-daemon
 2379 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
17729 pts/0    S+     0:00 grep --color=auto unity
```

---

### Post by lz1dsb on 2012-01-26
I had this "strange" hang once again today (well during the past few weeks more than once ;) ) so I found this:
I pressed Ctrl+Alt+F1 to get into the command prompt(my keyboard is blocked for everything else, but this key combination seems to work).
After getting into the command prompt I got back to my desktop session with Alt+F7 and ...voila the problem was solved! For now...
Right now I'm not quite sure if this is really a workaround but I'll try it out the next time it happens, because I'm sure it will hang again... 
I'll update this thread with the results...


Cheers,
Boyan

---

### Post by lz1dsb on 2012-01-28
I'v got this hang again today. Again I was able to recover from it using the loging into a console session and getting back to my desktop session...

---

### Post by RJARRRPCGP on 2012-01-28
I would suggest using htop and keeping it open to monitor reported CPU usage.

I heard that throttling processors can cause the OS to report high CPU usage, even when there's the same amount being used. 

I would check the core temps.

---

### Post by lz1dsb on 2012-01-31
> **RJARRRPCGP said:**
> 
I would check the core temps.

How do you i check the core temps?

---

### Post by Raevyn on 2012-01-31
lz1dsb,

I just installed Ubuntu 11.10 today with Unity and yes, I am indeed having the same issue as you. Odd hangups.. as though the system freezes for a few moments then continues on.

Now I am using it virtually using VMware 8 but my computer is fairly powerful. What I found more interesting is that the host computer is not having any issues when Ubuntu does the odd freezing. There is no sudden jump in memory, or even a jump in cpu and hard disk activity. It just.. hangs there for a moment. 

Its bizarre.

---

### Post by lz1dsb on 2012-02-02
Indeed it's bizare. I hope it will get resolved in time...
Did you try the "workarounds" I've used? Did it work for you?

---

### Post by lz1dsb on 2012-02-18
This strange freeze happen again today. 
Again I was able to recover by switching to the console Ctrl+Alt+F1 and than going back to my desktop session Ctrl+Alt+F7...
So far I have been upgrading my machine regularly...

---

### Post by lz1dsb on 2012-03-19
The freeze happened once again today. And again I'm able to recover after logging into the console and back into my graphics display session...
Am I the only one who experiences this?

---

### Post by RJARRRPCGP on 2012-03-29
> **lz1dsb said:**
> The freeze happened once again today. And again I'm able to recover after logging into the console and back into my graphics display session...
Am I the only one who experiences this?

Could be a Flash issue. 

I plan to dump Flash for YouTube! Most videos now appear to be fine with HTML5 & WebM.

Been using Debian Squeeze with Firefox 11 compiled with "march=prescott", FlashVideoReplacer extension and MPlayer.
I use MPlayer when I can't get a YouTube video to play in HTML5. Some videos fail to come up with HTML5. :(
That combo rocks! 

VLC sux! Keeps rebuffering when my internet service is fine.

---

