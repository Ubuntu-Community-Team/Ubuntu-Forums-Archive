---
title: "flash video SUCKS"
date: 2009-05-27
forum: General Help
---

### Post by rmausser on 2009-05-27
bit of a rant here, but also asking for help if you can get past my rant. 

Flash video for linux SUCKS. It SUCKS. I don't care what you say it sucks. 

I've had Ubuntu on 5 different computers, with both the 32 bit and 64 bit alpha, one computer is a quad core 2.6ghz machine with an Nvidia geForce card and 1024mb of video ram. 

HD flash plays on that thing like its a 486. 

Tried both with video acceleration enabled/disabled and compiz disabled. Still CHOPPY, skittery, buffery, shitty quality. 

Don't even talk about fullscreening your youtube videos. HA! 1 fps!

What gives, is adobe trying to sabotage us? 

If I load winblows on these machines they play flash videos like true champs. 

what gives man?

---

### Post by kelvin spratt on 2009-05-27
Flash in Linux is very good on my desktop, perhaps my graphics card is better suited and is set up, or I setup flash correct I use both 64bit and 32bit and windows and they all perform really well.

---

### Post by fillintheblanks on 2009-05-27
working good over here, it must be something on your end

---

### Post by lovinglinux on 2009-05-27
I agree. It sucks and the number of threads complaining about it is huge.

These discussions might help:

[http://ubuntuforums.org/showthread.php?t=1146943](http://ubuntuforums.org/showthread.php?t=1146943)
[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)

---

### Post by ActiveFrost on 2009-05-27
Can't say it sucks, but yeah, it's pretty slow ! Tested all sets of flash players on 2 different video cards ( both are pretty heavy ) and result is always the same .. video is slow and sometimes I even can't switch to HD mode ( YouTube ).

---

### Post by rmausser on 2009-06-05
I'm not asking for help here, or tons of different ways I might 'fix' this. I know what the problem is. 

I have Compiz running and am using Restricted Video Drivers. 

Still, in WinBlows Vista, this was never a problem. 

I am just hoping to create some controversy as I personally believe that if Canonical wants to create an OS that is competitive to Windows, this is the first thing they need to fix.

The one thing the average user now wants is streamed flash video working perfectly from the get go in their OS. HD or not, although more and more users want HD. 

Flash should work perfectly from the get go, imo.

I don't know if this is a problem with Firefox, the Flash plugin, Nvidia Drivers, or compiz using too many resources...but I really think it needs to be fixed. 

Thanks

/Rant

---

### Post by philinux on 2009-06-05
> **rmausser said:**
> bit of a rant here, but also asking for help if you can get past my rant. 

Flash video for linux SUCKS. It SUCKS. I don't care what you say it sucks. 

I've had Ubuntu on 5 different computers, with both the 32 bit and 64 bit alpha, one computer is a quad core 2.6ghz machine with an Nvidia geForce card and 1024mb of video ram. 

HD flash plays on that thing like its a 486. 

Tried both with video acceleration enabled/disabled and compiz disabled. Still CHOPPY, skittery, buffery, shitty quality. 

Don't even talk about fullscreening your youtube videos. HA! 1 fps!

What gives, is adobe trying to sabotage us? 

If I load winblows on these machines they play flash videos like true champs. 

what gives man?

This has nothing to do with flash and all to do with bandwidth. If you let an HD short movie play then keep the page open after it's completed but look in /tmp and play the flash video file from there it plays absolutely spot on.
It's youtubes and your isp's bandwidth problem.

---

### Post by Tibuda on 2009-06-05
> **rmausser said:**
> I am just hoping to create some controversy as I personally believe that if Canonical wants to create an OS that is competitive to Windows, this is the first thing they need to fix.There's nothing Canonical can do about it. They don't have the Flash Player source code. Adobe is supposed to do something about it, because they have the code. They are Linux foundation members, but I can't see why.

---

### Post by lovinglinux on 2009-06-05
> **philinux said:**
> This has nothing to do with flash and all to do with bandwidth. If you let an HD short movie play then keep the page open after it's completed but look in /tmp and play the flash video file from there it plays absolutely spot on.
It's youtubes and your isp's bandwidth problem.

This has nothing to do with bandwidth. These flash problems happens even with the video fully cached. If you play the video with YouTube player, it stutters and CPU usage goes to the roof. If you open the video from tmp folder or download it and play with VLC it plays flawlessly. This a problem with the flash plugin itself.

---

### Post by MikeTheC on 2009-06-05
No problems here at all. Works like a champ. Can't tell the difference between watching Flash videos in Linux, Windows or Mac OS X, both in standard and HD modes.

---

### Post by blueridgedog on 2009-06-05
My only complaint about flash is that it periodically crashes my sound system and I need to reboot before I get sound again.  Adobe as a whole seems to be still very Linux shy...(people have begged for photoshop for Linux since linux began).

Perhaps it is time to reverse engineer flash or create a new standard format.

---

### Post by MikeTheC on 2009-06-05
> **blueridgedog said:**
> Perhaps it is time to reverse engineer flash or create a new standard format.
You mean like Gnash?

---

### Post by blueridgedog on 2009-06-05
Yes...fantastic.  I hope it works.

---

### Post by rmausser on 2009-06-13
I just think there should be a better program that monitors every single process within your computer and which portion of code is requiring the most CPU/GPU processing.

Then, the people that are having problems could pinpoint the problem and then in future avoid that particular developer/hardware at all costs. 

So, if we found out it was because of Adobe, well then try to use something like Gnash or some other plugin if possible. If we could figure out it was an Nvidia problem, then sell our nvidia cards and buy intel, and never buy nvidia again. If it was a problem with firefox, then use internet explorer (KIDDING!) 

and philinux, its not a bandwidth issue. It is a problem with some process somewhere within the Flash plugin that is requiring massive amounts of unnecessary computer processing. 

Whether its a compiz overlay, an overlay issue within the video card (I know my Nvidia card shoots up to 105 degrees when I watch videos, but that can be due to a program inefficiently operating due to bad code, and requiring massive amounts of processing power for no reason) 

I say those with bad flash plugin preformance post our specs and we can compare to narrow the issue down.


I am running an HP Pavilion Laptop with ubuntu 9.04 64-bit with Firefox 3 and the 64 bit flash 10, with minimal compiz enabled. 

My computer specs are

2.0 Ghz Amd Dual Core
4 Gigs of DDR 3 Ram. 
128 MB Nvidia Geforce 7150M with the 180 restricted Driver. (GPU running at 450MHz, Memory at 666MHz)

---

### Post by rmausser on 2009-06-14
update.

The new linux kernel combined with the latest firefox has fixed my problem partially. 

Flash videos play awesome for a while. 

The problem is that my GPU gets very hot, and goes into low power mode to stop the computer from overheating. This is not Ubuntus fault, but a fault with the design of my HP laptop, and a poorly built Nvidia card, which has been known to be problematic.

---

