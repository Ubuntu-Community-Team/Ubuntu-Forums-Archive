---
title: "Enemy Territory lock up?"
date: 2005-07-07
forum: Gaming &amp; Leisure
---

### Post by Cidated on 2005-07-07
the game locks up once i go to select a server to play from...
no idea what the problem is :X
help a noob out? :D

---

### Post by MappyH on 2005-07-08
I have the same problem when selecting filters  :-? 

Try this server browser [http://www.linuxgames.com/xqf/index.shtml](http://www.linuxgames.com/xqf/index.shtml) 

I think its in Universe too?

---

### Post by lotusleaf on 2005-07-08
[QUOTE=Cidated]the game locks up once i go to select a server to play from...
no idea what the problem is :X
help a noob out? :D[/QUOTE]

Have you applied the upgrade patch? That might help.

---

### Post by endy on 2005-07-08
If you use xqf, you should try Seth's packages which are the latest version.

[Link to post](http://ubuntuforums.org/showthread.php?p=216516#post216516) 

You need qstat and xqf.

---

### Post by Cidated on 2005-07-08
okay so i tried a couple times to get ET to work normally and connect to a server thru ET
i can load up et and it runs for a bit then it stops, locks up and then the screen goes black :(
any ideas?

---

### Post by endy on 2005-07-09
Can you run ET from a terminal and post the output after it's crashed? It may be a good idea to run it in a window for example: "et +set r_fullscreen 0". Also a little info on your graphics card could help.

---

### Post by peter07 on 2005-08-05
I have ''similar'' problem. When I'm playing Et after some time ( 5-10 minutes ) game hangs up. I always run ET from console. I've even tried playing in window mode("et +set r_fullscreen 0"). After game crash I must us hard reset (ctrl+c, ctrl+alt+f1..f7 doesn't work). What may couses my problems - my old Pc (A 1GHz, Gf2 MX) or something else ?? How I can make Et more stable??

---

### Post by endy on 2005-08-05
ET is pretty intensive on the system and I you will need to do a few tests to try and find the cause. Assuming the ET install is good and Ubuntu is stable apart from playing ET I would suggest it's a hardware issue.

Some possible causes I've seen:

Faulty PSU  -  Starving the system of a stable supply of power, test another if possible
Faulty or mixed RAM  -  Memtest86+ can find out
Overheating  -  Check if the fans are full of dust etc... check temps in BIOS after crash if possible

It could also be worth looking in the system logs  like /var/log/messages and the xorg log  in /var/log/Xorg.0.log for any error messages just before the crash.

Hope this helps somewhat :)

---

### Post by imnes on 2005-08-05
I'm experiencing the lock-ups too.  This happens accross distros so I'm guessing it's the latest release of the nvidia drivers to blame.  Haven't tried an older / newer version yet.  Is this only affecting nvidia users or other people having it as well?

Nick

---

### Post by peter07 on 2005-08-06
My PC sometimes is stable sometimes is not stable. I don't know what couses my problems. It could be hardware issue - but I must test what is broken.

1) I think, that I'm using stable supply of power. What test do you propose here??
2) I've tried memtest. I've started the test using: 
> memtest all command and after some time I've recived the error message:
> Allocated 845152256 bytes...trying mlock...Killed
3) Some details about overheating:

Standard temperature: 37 C / 98 F CPU, 43 C / 93 F System
After hang up :  48 C  / 118 F CPU, 40 C / 104 F System

I've modified my PC cooling system and it is working without the box. Some time ago I tested my PC stability in hight temperatures. It is crashing when temperature cross 54 C.

About GF 2 MX drivers - I'm using 1.0-7174 version. What drivers version do you propose. In Windows GF 2 should run on 4*.** version but on Linux ??

---

### Post by Hairy_Palms on 2005-08-06
latest version is 7667. 7174 is quite old. i runt et on ubuntu with no problems since i found that they have precompiled drivers in synaptic but i had probs when using official drivers.

---

### Post by peter07 on 2005-08-07
>  latest version is 7667. 7174 is quite old. i runt et on ubuntu with no problems since i found that they have precompiled drivers in synaptic but i had probs when using official drivers.

What should I do ??

---

### Post by peter07 on 2005-08-08
1) Possible software issues:

I've read about PunkBuster. Old verion could have bugs. I've manualy updated my PB (pbweb.x86)

>  ./pbweb.x86 

I've also tried changing pb_system to 1 ( in Et console )

>  /pb_system 1 

Game is still locking up. I've also tried playing on servers without PB - the same results.
I've changed screen resolution, I've played in window, I've played without the sound - the same results.

2) Possible hardware issues:

I've found memtest86. Memory tests last very long - since now I've made 3 default tests - no errors.
I wrote about overheating - this can't be the locks reason.

3) Possible driver issues:

Which of these drivers is the best for GF 2 MX ??

[http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

Please help me

---

### Post by imnes on 2005-08-10
I've tried a few different distro's, lately been on Fedora Core 4 64-bit for about a week and the lockups persist there.  So that narrows it down to either the 2.60 ET updates, or the latest nvidia driver causing it.

Any non-nvidia useres experiencing the lockup?

Nick

---

### Post by Gnobody on 2005-08-11
My brother has this same problem on all operating systems he has tried.  I *think* it may be his on-board sound because sometimes I have to kill ESD to get it to run in Linux.  But even when he used to run it Windows it did the same thing, so I don't think it is how any of the sound servers are setup.

---

### Post by peter07 on 2005-08-12
> I *think* it may be his on-board sound because sometimes I have to kill ESD to get it to run in Linux. 
Have you tried playing with no sound?? I must try it, but first I must find how to turn off sound in ET console. 
> My brother has this same problem on all operating systems he has tried
What mainboard your brother use ??

---

### Post by endy on 2005-08-13
An idea just occured to me, *if* it is something to do with your motherboard a BIOS upadate *may* help but please don't do this unless you know that if it goes wrong your motherboard could be screwed. 

Oh and "et +set s_initsound 0" will start et with no sound. 

I hope you find out what's causing the problems ;)

---

### Post by peter07 on 2005-08-14
> Oh and "et +set s_initsound 0" will start et with no sound. 

It doesn't work. Et without the sound is sitll unstable. 

BIOS upadate may help, but with my lucky everything could go wrong.

---

