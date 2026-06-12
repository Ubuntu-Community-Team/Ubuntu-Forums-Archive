---
title: "Ubuntu 10.10  SLOW"
date: 2010-10-10
forum: Desktop Environments
---

### Post by xCloudX on 2010-10-10
Today I made a fresh install of 10.10, its really SLOW, with 10.04 everything was great.

I think this has to do something with a graphics driver.
***WHAT IS SLOW***
-Maximising,Minimising, moving windows
-Scrolling down websites
-Apps menu
-Volume pop-up window (sometimes)
-Its weird, because I _CAN_ watch videos on YouTube with no problems
[CENTER]     *Visual Effects is on *Normal(like it was in 10.04)*,if I change it to *None* it doesn't make a lot of difference



[LEFT] LAPTOP SPECS (eMachines D620.............i know)
[/LEFT]
[/CENTER]

ATI Radeon™ X1200 Graphics
With up to 1919MB of HyperMemory™ supporting Shader Model 2.0, Microsoft® DirectX® 9.0

1024MB 800MHz DDR2 (1 × 1024MB)
Expandable to 2GB
2 DDR2 slots total, 1 DDR2 slot available

AMD Athlon™ 2650e Processor
64-bit processor with AMD HyperTransport™ 1.0 Technology
(1.6GHz, 512KB L2 cache, 800MHz FSB)

I know its not a super computer or anything but everything was great  with 9.04 and 10.04.

---

### Post by _michel_ on 2010-10-10
there is a thread with similar subject:  check it out:   **[COLOR=#980101][B][ubuntu]**[/COLOR] 10.10 runs slow and jerky

[/B]

---

### Post by xCloudX on 2010-10-11
yeah, i did saw it, no proprietary drivers are listed in my pc.

---

### Post by vek on 2010-10-11
> **xCloudX said:**
> yeah, i did saw it, no proprietary drivers are listed in my pc.

Have you tried installing any?  Using the manufacturer (ATI) driver could help).  Not sure what kind of graphics card you have though, or how to install it... I figured the system->administration->additional drivers menu would offer to install it for you?

---

### Post by xCloudX on 2010-10-11
> **vek said:**
> Have you tried installing any?  Using the manufacturer (ATI) driver could help).  Not sure what kind of graphics card you have though, or how to install it... I figured the system->administration->additional drivers menu would offer to install it for you?

Yeah, i tried the ati website but didnt find anything, on the Additional Drivers, nothing is listed......

so is this a graphics problem or what:confused:

:(

---

### Post by wad4ever on 2010-10-11
Mine is slow now too, and I'm running with 4 CPU cores, 8GB RAM, and an NVidia video card in this Lenovo Thinkpad W510 laptop. Using the 64-bit version of Ubuntu 10.10 and compiz. It was speedy right before the dist-upgrade.

---

### Post by xCloudX on 2010-10-11
> **wad4ever said:**
> Mine is slow now too, and I'm running with 4 CPU cores, 8GB RAM, and an NVidia video card in this Lenovo Thinkpad W510 laptop. Using the 64-bit version of Ubuntu 10.10 and compiz. It was speedy right before the dist-upgrade.

You know, its things like this that make me think why not take the winXP/7 installation cd right next to me and put it in the cd tray, but then i remember......no AV with ubuntu lol.

no but seriously this sucks. I was excited about 10.10, you know, got up early to download, install and download my apps, but instead I get a slow piece of garbage, I KNOW the fault is probably 99.99% hardware, but I mean with 10.04 everything was good....... I might have to roll back to 10.04 if I cant fix it or if  you guys cant help me.

---

### Post by cgroza on 2010-10-11
Install htop and take a look what is taking your CPU.

---

### Post by xCloudX on 2010-10-11
> **cgroza said:**
> Install htop and take a look what is taking your CPU.
I used the *top* command on the terminal, everything seems fine, firefox is the most demanding process currently running.

---

### Post by cgroza on 2010-10-11
How many % the CPU is busy?

---

### Post by xCloudX on 2010-10-11
> **cgroza said:**
> How many % the CPU is busy?
i wish i could tell you, i cant find and indicator with CPU% usage, however there is a column with CPU% usage per process.

---

### Post by PabloTempe on 2010-10-11
I have an HP Laptop with an Nvidia graphics card and an AMD Athlon 64 processor (the last laptop on earth to have that combination, I'll bet!) running 64-bit Ubuntu Studio. There's definately a refresh of the graphics-handling with this release. At first, my graphics card wouldn't work in hi-def graphics at all and kept crapping out to the terminal output.
 
I escaped at boot, chose the low-fi graphical interface and had to remove the Nvidia legacy driver I had installed before (even though it showed as not being present). Re-installed the driver and appear to be up and running snappier than before, but I haven't put it through a proper burn-in yet.
 
But, definately something up with all the graphics drivers this release. They had some major problems to fix with certain intel graphic chip sets, I know that.
 
I also heard that ATI released some graphic card data recently, so aren't there any graphic driver choices for you having an ATI card now?

---

### Post by xCloudX on 2010-10-11
> **PabloTempe said:**
> I have an HP Laptop with an Nvidia graphics card and an AMD Athlon 64 processor (the last laptop on earth to have that combination, I'll bet!) running 64-bit Ubuntu Studio. There's definately a refresh of the graphics-handling with this release. At first, my graphics card wouldn't work in hi-def graphics at all and kept crapping out to the terminal output.
 
I escaped at boot, chose the low-fi graphical interface and had to remove the Nvidia legacy driver I had installed before (even though it showed as not being present). Re-installed the driver and appear to be up and running snappier than before, but I haven't put it through a proper burn-in yet.
 
But, definately something up with all the graphics drivers this release. They had some major problems to fix with certain intel graphic chip sets, I know that.
 
I also heard that ATI released some graphic card data recently, so aren't there any graphic driver choices for you having an ATI card now?

As far as I know, ATI has dropped support for the X1200 graphics card long time ago.(cheap-*** graphic card, lol)
You think reinstalling could fix this? (I don't think so, since it looks like its a driver issue)

---

### Post by vek on 2010-10-11
It sounds like the video drivers did not get activated for a bunch of folks.  For me it upgraded to nvidia 260.xxx automatically but that might be because I never manually installed any drivers... if you ever manually installed drivers, those ones might be taking priority.

Otherwise, the drivers are supposed to show up in the "System->Administration->Extra drivers" menu... at least for NVIDIA.  I'm not sure about ATI.  

You can type "glxgears -info" in the console to see what driver it thinks you're currently using.  I think glxgears comes with ubuntu...

---

### Post by xCloudX on 2010-10-12
> **vek said:**
> It sounds like the video drivers did not get activated for a bunch of folks.  For me it upgraded to nvidia 260.xxx automatically but that might be because I never manually installed any drivers... if you ever manually installed drivers, those ones might be taking priority.

Otherwise, the drivers are supposed to show up in the "System->Administration->Extra drivers" menu... at least for NVIDIA.  I'm not sure about ATI.  

You can type "glxgears -info" in the console to see what driver it thinks you're currently using.  I think glxgears comes with ubuntu...
I've never installed any drivers, I just throw the cd into the cd tray, and fresh install, like  I did with 9.04, 9.10 and 10.04 and everything worked GREAT, until now.....:(

btw, nothing shows up on the *Additional Drivers *menu. like it did before.
and about glxgears, it says I dont have it installed.

---

### Post by spiderman05 on 2010-10-12
I have just upgraded to 10.10. The new distribution is very slow (compared to 10.04). I have a Toshiba Satellite C650D. I removed, then activated the proprietary ATI driver, but this did not help. Menupopups take one second to open and applications take much longer to startup. Besides, I cannot play audio anymore. The only good thing is that my Ethernet card was working out of the box. 

I am really very upset about this. I am using this computer for work. Now, I have to re-install 10.04 and go through all the tweaking nightmares again. Maverick is still not stable enough to be installed.

---

### Post by xCloudX on 2010-10-13
> **spiderman05 said:**
> I have just upgraded to 10.10. The new distribution is very slow (compared to 10.04). I have a Toshiba Satellite C650D. I removed, then activated the proprietary ATI driver, but this did not help. Menupopups take one second to open and applications take much longer to startup. Besides, I cannot play audio anymore. The only good thing is that my Ethernet card was working out of the box. 

I am really very upset about this. I am using this computer for work. Now, I have to re-install 10.04 and go through all the tweaking nightmares again. Maverick is still not stable enough to be installed.

Same here bro, it sucks.
And for some reason, I keep hearing about ppl which have the same problem, and no one seems to have a solution.
Maybe they were so desperate to release it on 10/10/10 that they didn't got some stuff right.

---

### Post by destimond on 2010-10-14
This for shure will help you, read the information in this link:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

Use this PPA and then run atp-get update to fix the problem.

[https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc](https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc)

My issue was when minimizing and resizing, it was so laggy that it made me wanna uninstall ubuntu. But hey now all works just fine.

Hope this Helps!

---

### Post by xCloudX on 2010-10-15
> **destimond said:**
> This for shure will help you, read the information in this link:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568988)

Use this PPA and then run atp-get update to fix the problem.

[https://launchpad.net/~info-g-com/+archive/xserver-xorg-1.7.6-gc]("https://launchpad.net/%7Einfo-g-com/+archive/xserver-xorg-1.7.6-gc")

My issue was when minimizing and resizing, it was so laggy that it made me wanna uninstall ubuntu. But hey now all works just fine.

Hope this Helps!

Hey bro, thanks for your response, It looks Im reinstalling Ubuntu again, it was so unusable that i installed winXP (yeah, I was *that* desperate). And didnt installed 9.04, 9.10 or 10.04 because I was way too mad to Ubuntu, lol.

*"fixes a issue in xorg-server-core, that slows down the 3d performance of **proprietary drivers from ati**.*"

It says proprietary drivers, no driver was listed on the additional drivers menu, you think this will do it anyways?

:popcorn:

---

### Post by mr.tim on 2010-10-17
Hi,  just FYI / for what it is worth: I've also got an EMachines D620 which I had running "Netbook Edition" Ubuntu 10.04 initially, but upgraded this week to 10.10.

I think to be honest I'm going to revert back to netbook 10.04 version.

- performance is fine, as long as I don't try to use the Netbook launcher; I think something about the new bells-whistles GUI is breaking things.  The 'typical desktop ubuntu login' works fine for me. But I actually prefer the Netbook launcher in 10.04 to the 'default desktop environment' now after using it for a while.

- I wonder if you are using too many features / or a config that is too graphics heavy. Maybe check your login options at login time, try a few different things, see if it behaves differently ?

Certainl the general performance of Ubuntu on this system is very decent I've found. Despite being a 'low end laptop' with 'cheapo integrated graphics and a lower-end CPU'. (It is still a 64-bit modern athlon, despite the 1.6ghz clock .. it is pretty solid I'e found)

- my other general complaints: (a) Sound mute does not work when headphones are plugged in, speakers still play sound; (b) Sleep and lid-close doesn't behave right on 10.10; which worked better in 10.04; and additionally recovering from sleep (wake-up) fails quite often with 10.10 / which was not the case with 10.04

I think with the sleep issues, unless I find a fix, I'll be reverting back to 10.04 (fresh install, bother). 

So.  Hope this helps slightly.


Tim

---

### Post by Daxxi on 2010-10-22
Recent update (including kde-desktop) has improved things enormously, for me.

I've even enabled Desktop Effects, again. :)

Thanks!

---

### Post by Scott Deagan on 2010-11-08
There's a very long discussion about this here:

[http://www.ge.ubuntuforums.org/showthread.php?t=1592245](http://www.ge.ubuntuforums.org/showthread.php?t=1592245)

---

