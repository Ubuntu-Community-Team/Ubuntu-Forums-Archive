---
title: "Good experiences with aiglx and ATI? Anyone?"
date: 2006-11-08
forum: Desktop Environments
---

### Post by Ziggurat on 2006-11-08
Does anyone manage to have a smooth aiglx + beryl (or similar) with an ATI video card??

If so, how, wich driver (open, close), wich version?

Thanks.

---

### Post by SRParda on 2006-11-08
Yeah, I have installed two systems with Beryl and aiglx.

The drivers must be the open source (propietary don't support aiglx for now)

I had not big problems. With aiglx you can change the windows decorator inside a session with all your windows open if you are in trouble, sou you can be safe (remembering it's in beta of course).

The only problems I have seen are some 3D screensavers with music player visualizations running, and changing a lot of themes. It worked smooth (i don't use videos, that people see slower that with propietary drivers) with music player's visualizations.

---

### Post by pony-tail on 2006-11-08
Unfortunately I have been unable to use any of my Radeon cards with Aiglx as none of them function correctly (or 2 of them , at all )with the open source Radeon driver - X700 - no 3D , 9800XT no 3d , X800xt no video at all , X850XT-pe no video at all , the X800 and 850 cards both require "fglrx" drivers to be installed  before "x" will start . XGL and beryl an still be installed but AIGLX needs to be disabled first - Also AIGLX did not work correctly on my nVidia card with the latest beta drivers (the windows are just black ) so that machine Went back to "Dapper" at least it works.My experience with xorg7.1 and AIGLX is at least consistant at 100% negative on all machines I have tried it on (multiple Distros as well). I have been able to get everything working on most machines but not without major time and effort , much googling and reconfiguration . If you have only one machine and a lot of time it might be worth the bother but to roll it out on 8 or 9 machines it is a dead loss. Stick with "Dapper"

---

### Post by narcan on 2006-11-08
I've managed to get aiglx running with my Radeon 9600 XT pretty succesfully.

Here's the Device section from my xconf. I'm just using a standard install of Edgy.

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "radeon"
        BusID           "PCI:2:0:0"
        Option "DRI" "true" 
        Option "ColorTiling" "on" 
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "EXA"
        Option "XAANoOffscreenPixmaps"
        Option "RenderAccel" "true"
        Option "AGPMode" "4" #<- x may be 2 or 4 depending on your system
#       Option "AGPFastWrite" "on"  #<- Turning this on made the system crash
EndSection

Runs really well... faster than XGL. Only issues I've had are:

- Cannot use the Rain effects 
- Could not use xwinwrap for the desktop screensavers
- Video uses the normal color key overlay. Which is actually better imho for quality etc but means you don't get to see cool effects such as video being wrapped around a corner.
- TV Out. Everything went to hell when I started trying to get tv out working with the radeon drivers.

---

### Post by Ziggurat on 2006-11-08
Thanks for the replies, are you using beryl **narcan**?

---

### Post by narcan on 2006-11-08
Yes, I'm using beryl latest (0.1.2).

---

### Post by pony-tail on 2006-11-08
I guess my systems are a little "new" for fully gpl software (my oldest is a Soltek Qbic , 865ge chipset , 2.8/512/800 cpu , 1gig ram , 80g +120g .HDD , Radeon X700 /256 - AGP ) It is a couple of years Old but the graphics card is not (about a year) - The issue seems to lay exclusively with the Radeon's incompatability with the current Xorg - hopefully they will release a working driver (YEAH-RIGHT)

---

### Post by igknighted on 2006-11-08
> **pony-tail said:**
> Unfortunately I have been unable to use any of my Radeon cards with Aiglx as none of them function correctly (or 2 of them , at all )with the open source Radeon driver - X700 - no 3D , 9800XT no 3d , X800xt no video at all , X850XT-pe no video at all , the X800 and 850 cards both require "fglrx" drivers to be installed  before "x" will start . XGL and beryl an still be installed but AIGLX needs to be disabled first - Also AIGLX did not work correctly on my nVidia card with the latest beta drivers (the windows are just black ) so that machine Went back to "Dapper" at least it works.My experience with xorg7.1 and AIGLX is at least consistant at 100% negative on all machines I have tried it on (multiple Distros as well). I have been able to get everything working on most machines but not without major time and effort , much googling and reconfiguration . If you have only one machine and a lot of time it might be worth the bother but to roll it out on 8 or 9 machines it is a dead loss. Stick with "Dapper"

I have an x800GTO (core is actually the r480 from the x850) and I use the radeon driver exclusively.  It wont boot X at first because it defaults to 'ati' for the driver in xorg.conf, but if you boot in recovery mode and edit it to say 'radeon' instead (plus the other options narcan suggested) then x will boot perfectly and give you AIGLX

---

### Post by kvonb on 2006-11-08
I've been trying with my 9200se and had no luck.  Has anyone managed to get beryl stuff working with 9200?  If yes, could someone please point me to the relevant instructions.

Regards, Kev :)

oh, I'm running Dapper by the way.

---

### Post by igknighted on 2006-11-08
> **kvonb said:**
> I've been trying with my 9200se and had no luck.  Has anyone managed to get beryl stuff working with 9200?  If yes, could someone please point me to the relevant instructions.

Regards, Kev :)

oh, I'm running Dapper by the way.

To the best of my knowledge, that card only works in Edgy (X.org 7.1 w/ AIGLX).  The fglrx drivers don't allow the rendering necessary for XGL, or at least when I had that card the SuSE documentation I used told me that the 9200 was no-go with XGL.

---

### Post by kvonb on 2006-11-09
```
To the best of my knowledge, that card only works in Edgy (X.org 7.1 w/ AIGLX). The fglrx drivers don't allow the rendering necessary for XGL, or at least when I had that card the SuSE documentation I used told me that the 9200 was no-go with XGL.
```

Thanks for the info, I really don't understand what all the different AIGLX/GLX/XGL/Beryl acronyms mean, it's all Chinese to me!

From what you say above, and the little that I understand, I should switch to Edgy and install AIGLX then Beryl?

Sorry to be a pain, but is there a tutorial on how to do that?

I installed Edgy last week but went back to Dapper as the 8.28 driver (the last to support the 9200) that is supplied with Edgy has problems with Google Earth and Open Office (from my experience anyway).

All I really want is the drop shadows on my desktop, I don't need all the fancy stuff.  I do play 3d games (Wolfenstein/ET/BF1942/SoF/QuakeII/Glest) and from what I've read, if you install the ?GL? stuff it messes up 3d games, is that true?

Regards,  Kev :)

---

### Post by igknighted on 2006-11-09
Starting from the top:  As for the technical differences between XGL and AIGLX, I am not entirely sure.  AIGLX is a part of the X server, and there is nothing extra to install or hacks to add to your system.  Plus you can use 3D programs (like google earth or 3D games) at the same time.  To set up the open source radeon driver requires a little bit of configuration in xorg.conf, but check out this page for instructions: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).  After you enable what they suggest see the sticky on top of the General Support page for th beryl repo's.  All you need to do once the driver is working properly is install beryl and run it, there is no special session to create.  If you want to disable the effects you can kill the process and your session will continue without the effects.  Goodluck!

---

### Post by CarpKing on 2006-11-09
XGL does work with fglrx, at least in Dapper.  I have heard of fglrx in general being buggy in edgy; I haven't been using it since the upgrade, so I don't know how this affects your chances of getting it running.  If the open source drivers + AIGLX work for you, that's probably the best way to go.  AIGLX will not work with fglrx, because fglrx lacks some feature that AIGLX requires.

---

### Post by kvonb on 2006-11-09
Thanks igknighted, I will give it another try later.  I installed all the Beryl stuff a while ago so all I should have to di is change my driver.

Sorry if I hijacked the thread :D

Regards,  Kev :)

---

### Post by kvonb on 2006-11-09
Oh well, failed again :(

I lost direct rendering and the dreaded "Mesa Monster" raised it's ugly wart covered head yet again!

Seems like I'll just have to wait until I can afford a newer nvidia card.

---

### Post by igknighted on 2006-11-09
> **kvonb said:**
> Oh well, failed again :(

I lost direct rendering and the dreaded "Mesa Monster" raised it's ugly wart covered head yet again!

Seems like I'll just have to wait until I can afford a newer nvidia card.

hmmm, one more thought, did you remove the fglrx kernel modules after you edited xorg.conf?  ```
sudo rmmod fglrx
```... that and uninstalling the fglrx drivers (if you haven't already) are the only things I can think of at this point.

---

### Post by SRParda on 2006-11-09
No problem with new hardware.

I try with some of the latest:  Core 2 Duo with G965 chipset . And an X300 ATI Radeon (modern but not so lastest).

With radeon drivers and aiglx.


Not probed with fglrx drivers and Xgl.

---

### Post by CarpKing on 2006-11-09
> **kvonb said:**
> Oh well, failed again :(

I lost direct rendering and the dreaded "Mesa Monster" raised it's ugly wart covered head yet again!

Seems like I'll just have to wait until I can afford a newer nvidia card.

Keep in mind, if you're trying to use the radeon driver, "Mesa" is what you're supposed to see.  It can be trouble getting direct rendering with it though.

---

### Post by kvonb on 2006-11-12
```
hmmm, one more thought, did you remove the fglrx kernel modules after you edited xorg.conf?
```

..you're right I didn't!

Has anyone had this working?  I've been trying for weeks and have got to the point where I've nearly had enough.  There are so many different threads on how to do it, it is very confusing.

This is my ideal setup:

I would like to have drop shadows on my desktop, AND I would like to play 3d games as well.  Is this possible with a (standard AGP) ATI 9200se?  Which driver should I use, should it be the official repo driver (xserver-xorg-driver-ati) or the ATI proprietary driver (xorg-driver-fglrx)?

Confused.....Kev :confused:

---

### Post by igknighted on 2006-11-12
Unless something has changed, fglrx & XGL is impossible.  I had a 9200 and it was on SuSE's original incompatible hardware for XGL, so unless more work has been done on it i think option is out.  Read [this]("http://help.ubuntu.com/community/RadeonDriver") page to help set up the radeon driver.  I have only done this off of a fresh install, so I don't know how to remove the fglrx driver, but there are some instructions on the page, don't know if it is enough though.  Check and see if you have direct rendering by running
```
glxinfo | grep "direct rendering"
```
Once you have direct rendering, on Edgy you just need to add the beryl repo's and install it, and then you can start it and stop it at will in a standard session (no special XGL session or other editing necessary).  If you are ussing Dapper, go back to the "one thread to rule them all, v2" which is stickied on the top of the "general help" forum for direction on installing AIGLX.

EDIT: I can't get to the website, but I think it is because the server is down rather than a bad link... I can't get to anything on the help.ubuntu.com page

---

### Post by kvonb on 2006-11-13
```
Once you have direct rendering, on Edgy you just...
```

Maybe that's why it's not working, I'm using Dapper :).

I tried Edgy and got 3d working, but only the 8.28 driver is available for Edgy and it has issues with desktop apps like Google Earth and Open Office, they just won't run :(.

That's why I stuck with Dapper.

---

### Post by CarpKing on 2006-11-13
> **igknighted said:**
> Unless something has changed, fglrx & XGL is impossible.  I had a 9200 and it was on SuSE's original incompatible hardware for XGL

XGL + fglrx worked quite well for me in Dapper.  I have a 9600, though, so it could be that there is some issue with the 9200 such that it would be on that list.  

That said, I've been quite happy with the open source driver in Edgy without XGL.  Getting direct rendering was a bit of a pain, though, and Beryl still doesn't seem to play nice with some things.  Google Earth is also slow.  I think I may still have some xorg tweaking to do.  But it sounds like the fglrx driver in Edgy has problems of its own.  

Back to the topic at hand, if think you have everything set up right but still don't have direct rendering, could you post your /var/log/Xorg.0.log?

---

### Post by igknighted on 2006-11-13
> **CarpKing said:**
> XGL + fglrx worked quite well for me in Dapper.  I have a 9600, though, so it could be that there is some issue with the 9200 such that it would be on that list.  

That said, I've been quite happy with the open source driver in Edgy without XGL.  Getting direct rendering was a bit of a pain, though, and Beryl still doesn't seem to play nice with some things.  Google Earth is also slow.  I think I may still have some xorg tweaking to do.  But it sounds like the fglrx driver in Edgy has problems of its own.  

Back to the topic at hand, if think you have everything set up right but still don't have direct rendering, could you post your /var/log/Xorg.0.log?

Yeah, the 9200 was an odd child I guess and just doesn't work... unsure why.

There is a way to use AIGLX in dapper, but I would recommend going to edgy for the best chance of success w/ beryl.  Forget about the fglrx driver completely, as it probably wont ever get beryl working on that card.  Your best bet would be beryl + edgy + radeon driver, using AIGLX.  If you do want to stick with Dapper, search around for a how-to on using AIGLX w/ dapper.  I've never tried it, but it is possible.

---

### Post by darrenm on 2006-11-13
> **narcan said:**
> I've managed to get aiglx running with my Radeon 9600 XT pretty succesfully.

Here's the Device section from my xconf. I'm just using a standard install of Edgy.

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "radeon"
        BusID           "PCI:2:0:0"
        Option "DRI" "true" 
        Option "ColorTiling" "on" 
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "EXA"
        Option "XAANoOffscreenPixmaps"
        Option "RenderAccel" "true"
        Option "AGPMode" "4" #<- x may be 2 or 4 depending on your system
#       Option "AGPFastWrite" "on"  #<- Turning this on made the system crash
EndSection

Runs really well... faster than XGL. Only issues I've had are:

- Cannot use the Rain effects 
- Could not use xwinwrap for the desktop screensavers
- Video uses the normal color key overlay. Which is actually better imho for quality etc but means you don't get to see cool effects such as video being wrapped around a corner.
- TV Out. Everything went to hell when I started trying to get tv out working with the radeon drivers.
 Exactly the same as me on all fronts. Nice to know its not just me then.

---

### Post by kvonb on 2006-11-13
Well....

I managed to get Beryl working (Dapper/ATI9200se/ATI 8.27.10 driver with 3d working), it worked twice for about 5 seconds the first time, then 30 seconds the second time!!!!

I am SO frustrated, it won't work again.  I changed nothing, tried to reboot, shutdown, it will not come back again!

It's like being thirsty in the desert and having a tiny taste of water!  Man that is annoying.

But here's a real kick in the pants:

I'm writing this from the Edgy live CD, onto which I followed all the instructions here:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

I didn't change the video driver, it is the Edgy default.

I now have rubbery windows/transparency/drop shadows/fade effects/box-switching-thingy all running on the LIVECD!!!!

Can you believe that?

Now I just wish I could save this config, as soon as I reboot I'll lose all the fabbo goodness :(.

Have a look at this screenshot:

---

### Post by Orval on 2006-11-24
I had Beryl up and running using fglrx and XGL, but Beryl crashed very often. I wanted to try with the open source drivers and AIXGL, but uninstalling fglrx did not work. Whatever I tried, direct rendering wouldn't return.

Last night I reinstalled Edgy, followed [THIS]("http://ubuntuforums.org/showthread.php?t=301364") guide and Beryl flies. No crashing until now.
Beryl with the open source drivers and AIXGL is faster and smoother than with fglrx and XGL. I have an ATI 9200.

---

### Post by SubTerRaiN on 2006-12-06
i managed to get it working: beryl + edgy + radeon driver, using AIGLX on my ati 9200. works pretty nice.

---

### Post by rflmnz on 2006-12-09
COULD SOMEONE HELP ME?!?!

I'm really disappointed with XGL, because it denies VMARE and java programs to run...

Could someone tell me how to install ATI non proprietary drivers and how to install AIGLX?? Does is necessary to reinstall beryl?? Thanks a lot...

My videocard is a X1300...

Sorry my english...

---

### Post by darrenm on 2006-12-10
> **rflmnz said:**
> COULD SOMEONE HELP ME?!?!

I'm really disappointed with XGL, because it denies VMARE and java programs to run...

Could someone tell me how to install ATI non proprietary drivers and how to install AIGLX?? Does is necessary to reinstall beryl?? Thanks a lot...

My videocard is a X1300...

Sorry my english...

Hello, advice will vary on this but I've found:

if you are on Dapper, upgrade to Edgy.

then change the driver in /etc/X11/xorg.conf to radeon instead of fglrx

thats it really. If you're on Edgy already just use the radeon driver and you should be fine.

What ATi card do you have?

---

### Post by igknighted on 2006-12-10
> **rflmnz said:**
> COULD SOMEONE HELP ME?!?!

I'm really disappointed with XGL, because it denies VMARE and java programs to run...

Could someone tell me how to install ATI non proprietary drivers and how to install AIGLX?? Does is necessary to reinstall beryl?? Thanks a lot...

My videocard is a X1300...

Sorry my english...

Unfortunately I don't think you can do this.  The radeon driver only supports 3D acceleration on ATI cards up to the x850, so I doubt this would help you.  Your best bet, if you really want AIGLX, would be to give it a trial run with you onboard graphics from your MOBO, and if you like it then try to pick up an NVIDIA card.

---

### Post by rflmnz on 2006-12-10
I think my videocard doesn't have onboard video (I didnt see the video output).... 

But is it possible to force run the mobo graphics only for Ubuntu? Thanks!

Ps.: People could develop some drivers to x1000 cards instead of obligate people to change theirs videocards...

Again, sorry my english..

---

### Post by rflmnz on 2006-12-10
Hehe...

I know it's off-topic, but do you know how to shrink he grub load time? (I'm tired to wait 10 sec to load.... I would like only 1 sec...)

Thanx!

---

