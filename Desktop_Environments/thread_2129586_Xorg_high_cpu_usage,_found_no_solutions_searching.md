---
title: "Xorg high cpu usage, found no solutions searching"
date: 2013-03-26
forum: Desktop Environments
---

### Post by mrule on 2013-03-26
I'm running ubuntu 12.10 using Gnome 3 shell. 
Xorg uses 80-100% CPU and the system isn't performing well -- 
OpenOffice is unusable and nautilus hangs a lot when I try to browse. 

The system has 8 cores and gets really good performance otherwise ( anything not graphical ), I do most of my work from the terminal so it usually doesn't matter, but I'd like to have a more usable system. I've searched and I've been really frustrated -- I've just found a lot of "confirmed" bug reports and can't find any solutions. The only thing I did see that looked promising was for Kde though, and it involved changing how Qt handles font rendering. If it helps the problem first appeared with upgrade to Gnome3.
I know Gnome doesn't even use Qt but maybe something similar is happening?

---

### Post by mrule on 2013-03-30
bump? 

My only thought would be to try to fix the graphics drivers and switch over to hardware acceleration but I know that, at least in theory, it should be possible to render a no-effects desktop environment with much less CPU than Xorg is currently using, so I suspect this isn't the whole story ( plus I can't really figure out how to fix graphics, they have been broken for almost a year now )

---

### Post by mrule on 2013-03-30
The CPU fans have also sounded like a jet engine. I remember this all started with an "Upgrade" a year or so ago and I've tried to fix it various times to great frustration. I'm hoping something like this is happening:
GPU drivers broken by an upgrade --> Xorg defaults to CPU rendering which is for some reason a lot worse than it should be --> CPU load goes high --> CPU fan speed goes high. The weird thing is the processors aren't even getting hot, never above 50 degrees, so I feel like the software to control the fan speed is also broken. But that's another topic for another thread. Oridinarily I'd accept all of this as "Linux is not good at some things" but IT ALL USED TO WORK VERY WELL in the past. In fact, everything seems to have gone south since the shift to Gnome 3 and the unity interface. 

Anyway, lets start with the graphics card again: I can see it with lspci

07:00.0 VGA compatible controller: NVIDIA Corporation NV43GL [Quadro FX 550] (rev a2)

---

### Post by mrule on 2013-03-30
I tried to install the driver from NVidia. I waited for the "low graphics mode" prompt and clicked "exit to console login". Then, the screen went black and stayed black for 10 minutes. The machine was unresponsive to keyboard input. I was able to log-in via ssh, and I ran the appropriate driver install from NVIDA for my card. After installation, I asked the machine to reboot. It got stuck about half way. I let it sit for 20 minutes then briefly pressed the power button. The machine continued with shutdown and made it to "halt" although it could not power cycle itself on its own. I pressed the power button again and the machine shut down. Now... I am attempting to turn on the machine. It cannot boot anymore. It says 

"Error: missing /dev/dahdi"

a few more things seemed to load after that, though it is stuck after "starting PostgreSQL 8.4 database server"

So, in summary, my machine was laggy and unresponsive and Xorg was eating a lot of CPU. I tried to install the appropriate graphics card driver and my system appears to be completely broken now. 

:cry:

---

### Post by dabl on 2013-03-30
Did the nouveau driver not work?

That older nvidia card probably needs one of the "legacy" packaged nvidia drivers.  There are some other issues to be aware of:

[http://askubuntu.com/questions/225774/12-10-nvidia-driver-issues](http://askubuntu.com/questions/225774/12-10-nvidia-driver-issues)

[http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)

[http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/](http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/)

---

### Post by mrule on 2013-03-30
Oh wow thanks ! that actually worked ! -- at least for getting the graphics card drivers installed !
( also also reinstalled ubuntu-desktop at the same time so we can't rule out that that had a similar impact )

Now we shall see if the high Xorg CPU issue persists, and whether this is indeed related to the "jet engine fan" and "unresponsive openOffice and nautilus" issues!

---

### Post by mrule on 2013-03-30
Follow up: Xorg CPU usage has been low for since getting working graphics card driver. I'm going to assume that rendering low graphics mode on the CPU caused this problem. I understand that, in theory, it should be possible to render a responsive desktop environment on the CPU, that this might not work well with Gnome and probably requires more careful optimization than the community has time for. So... problem solved I think ( though the CPU fan still sounds like a jet engine, that must be unrelated ).

---

### Post by mrule on 2013-03-31
Yes, problem solved, thank you !

---

### Post by BlinkinCat on 2013-03-31
Hi,

Don't forget to mark your thread as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - ;)

---

### Post by gordintoronto on 2013-03-31
If you're interested in seeing how hot things are, lm-sensors and conky can help. I wrote it up in Full Circle Magazine, issue 51, page 40.

---

