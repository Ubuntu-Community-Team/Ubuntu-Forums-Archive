---
title: "High xorg CPU usage (multiple monitors)"
date: 2009-02-20
forum: General Help
---

### Post by madsporkmurderer on 2009-02-20
I've been experiencing very high xorg cpu usage that is causing problems; it doesn't seem to be linked to any individual program- watching TV in kaffeine sits it at about 40%, loading anything that changes the screen a lot seems to put about 40% load on as well (calculator, amsn, mines takes a good few seconds at near enough 100%).

I have visual effects turned off.

It did go a bit odd a while ago during an update where xserver gave some errors but still started; it didn't have the normal ubuntu theme to it (had blue bars and lots of icons/buttons were different) but ran a lot quicker. Could there be some bottleneck in the theme system? (I have no idea how this works)

It may be down to my screen arrangement, I have a 17" crt @ 1280x1024, a 21" crt @ 1600x1200 and 2x 22" LCDs @ 1680x1050. Could this be the cause and if so what can I do about it? I've got 2x nvidia geforce 8400gs

Thanks,
Mike

---

### Post by [TCK] on 2009-02-21
No solution, but I think I'm going through the same thing.  A few wildcards though.  I'm running Kubuntu 8.10 + KDE 4.2 and have an ATI X1600 rather than Ubuntu and Nvidia.  Dual monitors, 1680x1050 and 1280x1024.  Was working perfectly until a few days ago where a pushed update has caused Xorg to go under considerably CPU load, especially when playing full screen video (estimated 8fps).  The desktop in addition is generally laggy.  Don't know what packages I updated but I'm pretty sure that something within the last week has caused this.  Though I don't use Desktop Effects normally I have been able to turn it on previously, now I get a message asking me to check my X configuration.

---

### Post by madsporkmurderer on 2009-02-27
I have had a search about and found a suggestion of turning useevents on in my xorg, I've tried it but it doesn't work. I'm not entirely sure if I put it in the right places (there's a hell of a lot of device sections).

I'd really appreciate it if someone could have a look, there might be other things that need cleaning up as well- I've got 2xgeforce 8400gs each with 2 monitors plus a ps2 mouse&keyboard and a second ps2 mouse&keyboard connected through a USB adapter.

Thanks a lot,
Mike

---

### Post by [TCK] on 2009-02-27
For what it's worth, I reinstalled in the end.  Hopefully you can come to a better resolution.  Everything pertaining to xorg just scares the bejeezus out of me.

---

### Post by Mike Greenwood on 2009-02-28
[CENTER][LEFT]Hi yaas, at Ubuntuforum.  This is my first input as I just joined yesterday.  I am also new to Ubuntu as well as being new to Linux.  So in terms of Ubuntu and Linux I am as green as my name suggests.  I am not new to computers, reading and problem solving.  I have the 100% CPU usage problem as well.
    I am using Release 8:110 (intrepid)/Kernel: Linux 2.6.27.-11-generic / Genome 2.24.1
    With 310Mb.7 Memory/Pentium 3 Coppermine processor
    With  5.6Gb free disc space
Like with other articles I have read my CP usage jumps to 100% causing system overload and system drag.  Utube stops briefly every minute or so.  As if to catch up.  I observed the System monitor and noticed a fall in the CPU usage percentage when ever I turned resources off.  CPU usage fell to about 20% on average.  Immediately I hit the resources tabs I could see the last seconds at 20% rise sharply to 100%.  Once at 100% it just stays there banging its usage against the ceiling, dropping about 98% occasionally (every 30 seconds).  Only my active applications are turned on which directed my focus to the fact it must be Xorg or Genome.  Having been a firefox user on Windows I was aware that it was always a bit of a heavy user for my hardware needing about 40% CPU.  I mention Firefox  as I have been reading article  after article since last night to find a solution and some people seem to blame Xorg, Some Firefox-Yes they along with Gnome are the only applications running on my computer so it appeared to be one of them.  I have noticed that Firefox keeps going to sleep.  Electrically speaking if a device repeatedly switches on a power usage peak may happen-(Quantum Theory MJG) due to the absence of parcels in the line.  The sender has to fill an empty line with parcels.  Therefore more power is required to fill the space at first before the system settles down to parcels(quantities) being delivered at minimal Deliverer output.  The point is, why dose Firefox keep going to sleep.  Yes I am new to Ubuntu as well as Linux so the question "Why does Firefox keep going to sleep may sound daft.  I appreciate that sleep is a Linux term for not in use.  But my Firefox switches off even when I am using it.  It is in reality not the sleeping which causes power usage surge but the waking-up (switching on).  I know form childhood experience that I do not like to repeatedly switch on and off a common simple household light switch rapidly due to the strange electrical noises I may cause.  I believe if I sustain the action I may break the action as the fuse will be overloaded due to delivery surge beyond the normal operating load ability of the fuse(Safey device).  Point repeated,-Both Xorg and Firefox both keep switching off and on (sleeping and waking)they both keep peaking up to 100% CPU usage before descending again to a usable level before switching off.  It looked to me as if the problem could have been the computor progarm it self.  
   Can I instruct the computor software to just keep the programs I wish to run-run and not to put them to sleep so often.
   More to the mystery is, if I type Top at the terminal I can observe that the Terminal data is not the same as the System monitor.  The uppermost CPU% usage is Xorg which peaks at about 50% every 20-30 seconds.  There is no evidence of power usage surges and knowing my computer I would see the Terminal data as looking kind of healthy.  This is where the circle (cycle) is completed (circuit complete).  It leads me back to the system monitor and the difference between the data of it self and the terminal.  Is everything really okay except for the system monitor which uses a process which shows on the scope as 100% CPU usage.  Is it itself using all that CPU usage.  Why do I get a massive rise when I switch from System Monitor Processors to Resources?
   I read other Linux system's Forums about 100% CPU usage and found many users had, were and are experiencing the same problem.   I observed it is not new either.  I read reports from 2008 with the same problem.  Hundreds of attempts have been made to change systems/to reinstall but they all report no complete eradication of the problem.  If of course someone has found an answer I would be glad to know, as would many others.  As may be observed form my little input I also do not have a solution but I do have the problem.     This input is a result of the many requests for others with the problem to speak-up.  I may at present be on the wrong track but one has to kiss a lot of frogs before one finds the princess.  I find it probably I will be criticised but only by pasing comment about my lengthy first input-but I assure my critics that this is brief my my standards.
   [CENTER]Regards From Mike (a new comer to Linux and Ubuntu)
[/CENTER]

---

