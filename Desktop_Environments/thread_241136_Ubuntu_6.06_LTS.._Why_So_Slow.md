---
title: "Ubuntu 6.06 LTS.. Why So Slow?"
date: 2006-08-21
forum: Desktop Environments
---

### Post by matt_risi on 2006-08-21
Hey folks, I've got a question. Here is my current setup:

HP Pavilion 7845
800mHz processor, upgraded to 256 mb RAM, 40 gb HD.

In threads I've seen the above distro run smoothly on much lower spec'd systems. It runs not REDICULOUSLY slow on this computer, but slow enough for it to be a nuisance. OpenOffice, Add/Remove, Rhythmbox, Firefox etc loads very slowly and at some points there are some serious hang times. Is there something I'm doing wrong?

Thanks very much.

---

### Post by BitTorrentBuddha on 2006-08-21
Have you tried Xubuntu, it uses XFCE, it's a more light-weight window manager than GNOME.

---

### Post by encompass on 2006-08-21
Your computer is slow...  Have you tried running Xubuntu... a special version made to run a little lighter.
And you REALLY not alone on that OpenOffice... they need to really speed things up there.  I try to use different stuff for my office things when I can avoid it.
I use xubuntu on my 700mhz Celeron from HP/Compaq 200mb RAM and 10GB HD

---

### Post by b_martinez on 2006-08-21
Just out of curiousity, how much swap space do you have on this hdd? On your system, you will need {read "should have"} 512 MB . And the suggestions about XFCE are good ones. I use it on a Debian installation, Intel 433 MHz,198 RAM, 10Gig HDD. Works faster than the old Win98 that was on there. If you opt to install XFCE rather than install Xubuntu, you can get rid of some of the Gnome stuff, but be careful, as another person on this forum used apt to un-install Gnome and took the Gnome Desktop [ or is it display?] Manager along. Now he has no GUI.

---

### Post by true_friend on 2006-08-22
oooooooooooooooooo
so it is.
i am trying to migrate to kde with removing gnome at all. it means there is a system crashing risk.
:( :(

---

### Post by true_friend on 2006-08-22
and it is true ubuntu is so so slow.
i have 1.8 GHz intel processor 40 GB mextor HDD and 256 MB memory and struggles when two or more softwares runs.
i.e. Akregator + fire fox just restarted my system it was hanging.
is it due to a lot of packge downloads.
i have 400mb+ packages downloaded in which kde is also included. should i have to clean them all to speed up system??

---

### Post by matt_risi on 2006-08-22
I've used Xubuntu in the past and it just doesn't compare to the features and asthetics that are present in Ubuntu. I guess I'm just kinda disappointed because Windows 2k ran MUCH faster on this machine than Ubuntu does. Perhaps I'll try installing X.

---

### Post by compwiz18 on 2006-08-22
> **true_friend said:**
> and it is true ubuntu is so so slow.
i have 1.8 GHz intel processor 40 GB mextor HDD and 256 MB memory and struggles when two or more softwares runs.
i.e. Akregator + fire fox just restarted my system it was hanging.
is it due to a lot of packge downloads.
i have 400mb+ packages downloaded in which kde is also included. should i have to clean them all to speed up system??
I've got a 1.8GHz processor too, and I can open hundreds (literally, I tried it once - got to about 150 before I got bored, but Ubuntu still ran smooth as slik) of apps with 1GB of RAM...so if you wanna think about an upgrade (RAM)...that would speed it up.

---

### Post by true_friend on 2006-08-25
hmmmmmmmm
i am also thinking to upgrade my ram to double of orignal one in a few months. the software dependencies i think slow the system. a little about40 kb software requires 15 MB of dependencies. specially in gnome. now on kubuntu and working every thing smoothly. trying to avoid install any thing out of kde. but synaptic and opera which i have to use occeanly. and not also firefox it is based on gtk simply my ram will be used more due to running firefox in kde it will load its own libraries to be executed.
so my experience try to be in the desktop enviroment u are using or upgrade ur ram to atleast 512 MB.

---

### Post by Greycloak on 2006-08-25
If there is one commonality between all of the above complaints, it's that everyone who is complaining about slow performance has 256mb or less of RAM.  I'm running on 512mb and it seems like Ubuntu runs much faster than windows.

---

### Post by JKoder on 2006-08-25
Just for my information.. what release of ubuntu do you use ?
Perjaps Ubuntu 6.06.1 ??? If so  YES this one runs EXTREMLY slow on my laptop to (Amilo L7300 1.5 G, 256 )
Earlyest Ubuntu releases ware great .. but this 6.06.1 is noyt so good :(

---

### Post by asplode on 2006-08-25
I run Xubuntu 6.06 on this system:

AMD Athlon XP 900mhz
192MB RAM
S3 Virge 4mb Graphics Card
ASUS K7M Slot A Motherboard

And while it starts slow as the bejeezus (about a minute or two, it helps to walk away from it while its starting) once XFCE is up and running, its a fantastic computer.

I've surfed the web with a dial up modem, and I've never seen dial up go faster.  I've done graphic design work in GIMP, and it was much much faster than I ever expected it to be.  Not quite on par with my 3ghz system, but not too far behind it either.

---

### Post by bluenova on 2006-08-26
I have a 1Ghz Athlon with 512Mb SDRam and nVidia Card with the nvidia drivers.

When I fist installed Dapper after it's release it ran super fast, but gradually it seems to have slowed down over time (what, a few months?)

I now find running more than 2 apps really slows the system to a halt especially if Java is involved. I thought the slow down effect was something only MS Windows suffers from? Short of doing a re-install is there any way I can get my system running nice again? 'top' shows that apps are running ok and not hogging resources, it just seems to be a general system wide thing.

---

### Post by mgmiller on 2006-08-27
First, everybody needs more ram.  512 minimum, 1 gig or more better.

For the general slowdown, look in System>Administration>System monitor and see if something is hogging cpu cycles.  Under Edit>Preferences, in the Prosesses tab, in the Process fields window, make sure CPU time is checked, I think by default it is off.  If something is hogging CPU, then you can come back here and search for a solution to that.  

I noticed you said top showed nothing hogging CPU and the problem was worst with java running.  In a terminal Type:
```
sudo update-alternatives --config java
```

This will show you which versions of Java you have and allow you select which one to use.  I have found the sun java to work better than the others.  If you don't have sun java you can install it easily from easyubuntu.
I have Ubuntu machines running 24x7 for over a year with no slowdowns, just occaisional reboots for kernel updates and stuff.

As far as Open Office goes, run the word processor and go to tools>optons.  Click the + next to OpenOffice.org and then highlite the word Memory.  To the right of that put a check mark in the box under OpenOffice.org quickstarter.  Click ok.  Now when you try to open an openoffice doc or anything else in OO, it should be almost instantaneous.  On my system, it's up before I can let go of the mouse button.  

I can't stress enough...It helps to have as much memory as you can afford.  256 is simply not enough for a modern OS.  This includes WinXP.  I have used machines that way, (AMD K6-2 500 MHz) and you can brew coffee waiting for it do anything.  Adding another 256 for a total of 512, was like buying a new computer.  If you have at least a 1 gigHz CPU and 512MB-1 gig of ram, I think you will find Ubuntu 6.06 is not slow.

---

### Post by bluenova on 2006-08-28
Hi mgmiller,

Thanks for the reply. Unfortunately 512mb RAM is the most I can have on my current board, but when I first installed Dapper it ran very fast. I am normally using about 480 RAM / 0 Swap with 2 users running, perhaps this is not right?

I have checked Java and the default is set as java-1.5.0-sun. With regards to CPU hogging, the only thing constantly using the CPU is XORG (15-30%). I have the Nvidia (repository) drivers installed and working. I've tried going back to the original XORG that shipped with Dapper but that makes no difference.

---

### Post by dentaku65 on 2006-08-28
I've foud Desktop Optimization very very useful... unfortuately is not in the repo, but is quite simple to install/use:

[http://yep.it/?1tgsiw](http://yep.it/?1tgsiw)

8-)

---

### Post by bluenova on 2006-08-28
Thanks for the the link dentaku65, but I'm pretty sure my problem is Xorg related, I just don't know how to solve it.

---

### Post by bluenova on 2006-08-30
Well the problem was getting a bit too much to bare, so I've done a fresh install. I wanted to rearrange my partitions anyway. The system is now running at a good speed again, but XORG still uses 15-30% of the CPU so I guess it was not the problem. I think it is just a case of having installed/uninstalled a lot of programs while trying them out. It seems Ubuntu suffers from the same problem as MS Windows, with the slow-down effect.

---

### Post by carontis on 2006-08-30
I've installed Ubuntu 6.06.1 on a laptop of a friend and believe me it's a real speed. The pc is a Fujitsu Siemens with an AMD 2000+ (not such a big cpu...). After installed I tried to check if everything was ok, and so it was. Now that friend doesn't want hear anymore about windows..! Probably your installations are depending from architectures of machines you have. After seen this one I prepared, I  can only say that Ubuntu is the actual best distro. Hope it will continue this way.

---

### Post by mgmiller on 2006-08-30
bluenova, you wrote:  > I am normally using about 480 RAM / 0 Swap with 2 users running, perhaps this is not right?

I think this may be your problem.  I have found a thread where they discuss a problem with the swap partition not being enabled and causing problems with x.org consuming more and more memory, resulting in slowdowns and freezes.  I have 2 gig of ram and even with just 1 or 2 apps running, some of my swap file is always in use.  
in a terminal type the command ```
top
```
the 5th line will show your swap status.  Some of it should be used, it it's zero, I think you have a problem.
Read through the thread and you may get some pointers.  The name of the thread is "Dapper freezes 1-3 times a day"  You could enter the thread name, without the quotes in the search box at the top of the dapper forum page if the link below doesn't work.  
[HTML]http://www.ubuntuforums.org/showthread.php?t=193283&highlight=swap+partition[/HTML]

---

