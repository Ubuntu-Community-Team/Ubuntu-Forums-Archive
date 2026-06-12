---
title: "Horrid Lag in Ubuntu 9.04 (AMD64)"
date: 2009-04-26
forum: General Help
---

### Post by NekoMaster on 2009-04-26
I use to like ubuntu, I use to like it alot since it ran faster and crashed way less then windows. BUt now things have changed, I installed 9.04 (amd64) and everything is sloooow, theres so much lag and crashing Im starting to hate ubuntu. Its not a video card issue as im not doing anything that uses my video card much, other then trying to play openttd.

This thing has so much lag and crashes so much I might as well stayed with windows 7 build 7068 (32bit) as that ran much smoother.

I have a decnt dual core (AMD athlon x64 x2 5200+ @ 2.7GHz) with 4GB ram and this lag makes my PC feel like a peice of s***. whats going on here? Im not running anything other then pidgin and firefox,oh and I run inkscape a bit, but not alot cause of the LAG! What can I do to speed things up?

---

### Post by gta117 on 2009-04-26
spin around in your chair really fast for 3 mins. I guarantee you it will go faster, and your computer will look like its moving too!


Seriously though, I seem to have some problems like that too. But more with min and max windows. Try and see if with the new update something became incompatible. Any reg or files that you have running (like themes) might be slowing you down because of crapy code or like what I said before.


call back if you turn up with noth'n still


-gta117

---

### Post by Tipped OuT on 2009-04-26
I'm guess it's because of your processor? Also, if Ubuntu 8.10 worked well for you, then stick to that until they come out for a fix for your hardware.

---

### Post by gta117 on 2009-04-26
I am afraid for me, it is already to late...


-gta117

---

### Post by dcstar on 2009-04-26
> **Tipped OuT said:**
> **I'm guess it's because of your processor**? Also, if Ubuntu 8.10 worked well for you, then stick to that until they come out for a fix for your hardware.

What rubbish, I have 9.04 installed on my Athlon 64 system and it runs fine (as it did in previous Ubuntu versions) - like thousands of other AMD installs.

If there is a problem with a particular system then people here need specific details to try and find the cause of the problem, rather than just "lag".

---

### Post by gta117 on 2009-04-26
well... um some of us are hav'n troubs bro!


But like I posted above, it seems to be the update has made many programs incompatible. (Usually small ones, that prob slow ya down.)

-gta117

---

### Post by Tindytim on 2009-04-26
> **NekoMaster said:**
> **Its not a video card issue** as im not doing anything that uses my video card much, **other then trying to play openttd.**

I'm no expert, but I'd guess that would use your video card. :P

What card, and have you installed drivers?

---

### Post by NekoMaster on 2009-04-26
> **Tipped OuT said:**
> I'm guess it's because of your processor? Also, if Ubuntu 8.10 worked well for you, then stick to that until they come out for a fix for your hardware.

Its not my proccessor, it runs WinXP, Vista and 7 all fine, hell a 5000+ (2.6GHz) is able to run Ubuntu 8.10 just as fast!

> **dcstar said:**
> What rubbish, I have 9.04 installed on my Athlon 64 system and it runs fine (as it did in previous Ubuntu versions) - like thousands of other AMD installs.

If there is a problem with a particular system then people here need specific details to try and find the cause of the problem, rather than just "lag".

You make me angry for some reson >: (

> **Tindytim said:**
> I'm no expert, but I'd guess that would use your video card. :P

What card, and have you installed drivers?

DUDE! I just said it wasn't my video card! I know at the moment the drivers arn't perfected but that shouldn't be a problem just running the system it self! Im using a ATI Radeon HD 3200 (IGP with its own GPU and 1.6GB VRAM, 256 of it dedicated)

That thing has served me quite well when playing games like locomotion, openTTD, TES4 Oblivion, Halo, and Fallout 3, but right now Im not playing any games cause I lost them all except openTTD

Anyways, its not my video card, my CPU most of the time is being using 50% or more (or 1 Core at 100%) making it laaaag like hell. Im not even doing anything big, I'm just sirfing the web and chatting using pidgin. I also listen to music but everything keeps carshing so I can't really listen to more then a few songs before it stop and crashes :(

and this lag was here before and after any updates from the update manager. I seriously don't know whats going on here since when my PC get really lag system monitor show the CPU is in use but it doenst show what is even when I have nothing open!

---

### Post by Tindytim on 2009-04-26
> **NekoMaster said:**
> DUDE! I just said it wasn't my video card! I know at the moment the drivers arn't perfected but that shouldn't be a problem just running the system it self! Im using a ATI Radeon HD 3200 (IGP with its own GPU and 1.6GB VRAM, 256 of it dedicated)

That thing has served me quite well when playing games like locomotion, openTTD, TES4 Oblivion, Halo, and Fallout 3, but right now Im not playing any games cause I lost them all except openTTD
How do you know it's not a driver issue? I know from experience ATI cards don't play nice all the time. It has nothing to do with the specs of the card, or how well it may perform under Windows.

But other people appear to be having a similar issue, so I can't say. But it always helps to be detailed in describing the situation.

---

### Post by NekoMaster on 2009-04-26
> **Tindytim said:**
> How do you know it's not a driver issue? I know from experience ATI cards don't play nice all the time. It has nothing to do with the specs of the card, or how well it may perform under Windows.

But other people appear to be having a similar issue, so I can't say. But it always helps to be detailed in describing the situation.

how can it be a driver issue with my video card? I have visual effects off cause I dont need fancy shmancy effects to bog my system down. If it was a video car dissue then why would my CPU be getting 50% used or more causing Ubuntu to lag?

---

### Post by Arup on 2009-04-26
It sure does look like a video driver problem, you should use the one from the manufactuer's site or install via envy and also try and see with system monitor or top which particular app is stealing the CPU calls.

---

### Post by oobe-feisty on 2009-04-26
Im experiencing the exact same problem im running jaunty amd64 

with 2gb of ram 2 gb of swap and a 

AMD Athlon(tm) 64 X2 Dual Core Processor 5600 @ 2900 Mhz

i was running the beta and the rc and they ran fine i did a fresh install when it was released and now its gone to **** im thinking about switching back to 32 versions as i notice one of the problems is npviewer.bin sometimes taking up a lot of cpu usage plus i cannot play wmv9. 

i have had amd 64 processors since 2003 and every linux version that was built for amd64 i have had some issues with i was hoping to try it this time with no issues but instead of increased performance i have found the oppisite.

just my two cents i want people to take the original poster seriously and not suggest things such as it being his hardware or video drivers since that is not possible given the info he has already provided



EDIT:
i decided to downgrade my nvidia driver from nvidia-180-libvdpau to  nvidia-173-kernel-source
and that did the trick i appoligise it may not be the same issue for the original poster however this has remidied my problem

i dont really need vdpau just yet AFAIK i do not have mplayer vdpau version and i know the mythtv version im running does not support it yet

---

### Post by NekoMaster on 2009-04-26
> **Arup said:**
> It sure does look like a video driver problem, you should use the one from the manufactuer's site or install via envy and also try and see with system monitor or top which particular app is stealing the CPU calls.

I did that, helped a little bit, but no I have the problem of stuff like fire fox, pidgin, rythem box music player, and openttd crashing so much it sometimes forces me to hard reboot : (

Maybe I should just get the 32bit version, but then if I (and many other people) dont support 64bit OS'es then how will they ever develop to be a good system when the time comes that we are forced to use 64bit OS'es

---

### Post by xp2mac on 2009-04-26
> **NekoMaster said:**
> I use to like ubuntu, I use to like it alot since it ran faster and crashed way less then windows. BUt now things have changed, I installed 9.04 (amd64) and everything is sloooow, theres so much lag and crashing Im starting to hate ubuntu. Its not a video card issue as im not doing anything that uses my video card much, other then trying to play openttd.

This thing has so much lag and crashes so much I might as well stayed with windows 7 build 7068 (32bit) as that ran much smoother.

I have a decnt dual core (AMD athlon x64 x2 5200+ @ 2.7GHz) with 4GB ram and this lag makes my PC feel like a peice of s***. whats going on here? Im not running anything other then pidgin and firefox,oh and I run inkscape a bit, but not alot cause of the LAG! What can I do to speed things up?

I experienced the same problem after installing the final 9.04, and then I discovered that by updating the video driver on my laptop (toshiba satellite) everything is as fast as it should be.

---

### Post by rlonnborg on 2009-04-26
I would like to put my two cents in.....
I have a T42 Laptop that was super fast with previous Ubuntu.  This new 9.04 is crap.  It is dragging like a old lady.

Video in Mozilla are very choppy.

Program load time is stupid slow.

This was not ready for release.

---

### Post by oobe-feisty on 2009-04-27
Hi just reporting back it is a lot better since i downgraded my nvidia drivers but i think its slower than 8.10 32bit i dont know if its 64bit or juanty that is making a difference but things still seem slower on this install rc and beta were ok 

P.S will a developer quickly come and read this thread and accurately guess what is wrong based on the small amount of information given with and infinite number of unknown variables then create some fixes  and then add them into the repo all in one day 

thanks

---

### Post by oobe-feisty on 2009-04-27
NekoMaster 

do you have either of these packages installed

ia32-libs-tools  ia32-apt-get

---

### Post by El Zoido on 2009-04-27
Hm, I'm using the 64bit Version, too.

Allways used 32bit but I thought about giving it a try.
So far everything seems to be working fine for me (Intel C2Duo E4600, NvidiaGF9600GT), boot-time is much improved (from about 70 s total to 40 s), no performance issues except for one thing:

Firefox sometimes seems to lag. I think it has to do with flash.
I'm going to test a bit after installing Flashblock.

---

### Post by cybrsaylr on 2009-04-27
I'm having the same lag problem.
It may be an Ipv6 issue.
You may have to disable Ipv6.

Here's some advice on how that may help you 

[http://ubuntuforums.org/showthread.php?t=1139386](http://ubuntuforums.org/showthread.php?t=1139386)

---

### Post by cdbitesky on 2009-04-27
I had the same problem. Just installed 32-bit Jaunty on a computer with Radeon HD 3650. If i had the "Suggested drivers" activated the computer would freeze up and lag every time i changed a window. After having it crash 3 times, i turned it off and everything ran just as smoothly as 8.04 did. I am really sick of ATI and their horrible drivers.

---

### Post by marco123 on 2009-04-27
> **cdbitesky said:**
> I had the same problem. Just installed 32-bit Jaunty on a computer with Radeon HD 3650. If i had the "Suggested drivers" activated the computer would freeze up and lag every time i changed a window. After having it crash 3 times, i turned it off and everything ran just as smoothly as 8.04 did. I am really sick of ATI and their horrible drivers.

Same here, except I have an ATI HD3450.  With the restricted drivers enabled I would get massive system slowdown (xorg using 50% of one of the cores) when playing videos, although not every time.  I reverted back to the open source drivers and everything seems fine now.

Never discount a piece of hardware. :wink:

Cheers, Marco.

EDIT: Are you using an ATI card?  If not then this bug won't effect you.

---

### Post by NekoMaster on 2009-04-27
> **marco123 said:**
> Same here, except I have an ATI HD3450.  With the restricted drivers enabled I would get massive system slowdown (xorg using 50% of one of the cores) when playing videos, although not every time.  I reverted back to the open source drivers and everything seems fine now.

Never discount a piece of hardware. :wink:

Cheers, Marco.

EDIT: Are you using an ATI card?  If not then this bug won't effect you.

Sadly i am, imusing a OC'ed ATI Radeon HD 3200 IGP, 600MHz, 250MB dedicated vram

---

### Post by camper365 on 2009-04-27
I think that with Jaunty, there is a free software driver that comes for some NVIDIA cards, and they have removed the option for the proprietary driver.
Since the free software driver is so new, it may have issues.

---

### Post by Raskula on 2009-04-28
The only problem I am having with 9.04 is the incredibly laggy scrolling and laggy drag and drop pictures on websites. Thats about the only lag issue I am having.

---

### Post by Eneerge on 2009-04-30
I had that scrolling issue when I made a custom kernel.  However, OTB, I did not have the problem.  I'm not sure what the problem is exactly, but I swapped to a custom kernel and the problem went away.

Maybe you could try the 2.6.28-9 kernel.  AFAIK, the 2.6.29-2 isn't compatible with the ATI driver.

---

### Post by emarkay on 2009-04-30
> **NekoMaster said:**
> Its not a video card issue as im not doing anything that uses my video card much, other then trying to play openttd.


How can you confirm it's not a video card issue?

There is a BIG ATI issue in 9.04 (and also lesser Intel and NVIDIA issues). 

ATI ISSUE: [http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by ladydeth666 on 2009-04-30
Im having a very similar issue.....but using an Nvidia 8500gts, with an AMD 5400+ on an ASUS Sli board, on a 32bit 9.04 beta load.  Im getting laggy response in a terminal window with nothing running :) but something is maxing out my dual core cpu's in tandem.
If you are interested, heres the other thread thats been posted:

[http://ubuntuforums.org/showthread.php?t=1141241](http://ubuntuforums.org/showthread.php?t=1141241)

---

### Post by tombom62 on 2009-05-01
Same deal.  I hate ubuntu now.  Well, it's just too bloated, slow, and it broke my copmuter when I installed the RC 2 so I'm not even gonna try the final one.  Go to debian.

---

### Post by wo1fe on 2009-07-09
i am currently experiencing a similiar problem with my system. i switched to ubuntu because i was having serious issues with a clean install of win vista. (explorer.exe kept crashing causing me to loose all information on screen at the time). since i have switched the system has been running much slower and when attempting to play any sort of game that runs in fullscreen mode the entire computer gets very laggy. even when i am not attempting to play a game the system is very very slow to do something.

system specs.

amd64 dual core 6000+ 3.1ghtz

8 GB ram

Nvidia 9600gt (not the problem i was playing crysis just before i switched because i kept loosing where i was up to)

ASUS M2A-VM Mobo


from what every one has told me after thinking about this for awhile this system should be just as fast as it was with vista yet this is not the case. i am going to try downgrading the video driver and seeing what happens.

---

