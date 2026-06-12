---
title: "Why is surfing web with FireFox terribly slow on my PC ??"
date: 2007-12-31
forum: Desktop Environments
---

### Post by misko_ on 2007-12-31
Hello,

First my configuration:
P4 1500 MHz
750 SDRAM
160 GB HDD
ATI RADEON 9600

I use ubuntu 7.10, everything is fine, working normal except when I use Firefox to browse the web. My CPU end up to 100%, and by using top I see that Firefox is responsible. And when I say slow I really mean slow, checking gmail is terrible to open one e-mail take like 2 seconds and to make new label take up to 5 seconds. All this on XP was instant speed.

I have removed trackerd service, because it also was always at 50% of CPU [http://ubuntuforums.org/showthread.php?t=591867&page=2](http://ubuntuforums.org/showthread.php?t=591867&page=2) and I do not even need it...

Why is it so slow ? 
Is it possible that my PC to old ??? Does anybode asle use ubuntu 7.10 on thos configuration and what are his experiencec with browsing the newt ???
Or is is possible that something is not configured correctly ?? 

If you have any idea please put it...

Thanks...

---

### Post by foolsh on 2007-12-31
Do you have a swap file?
run 
```
free
```
and see if any exists.
did you install a lot of software lately?
has it always been slow this slow since you installed 7.1?

---

### Post by stijngysemans on 2007-12-31
maybe it is a problem with the flash player.
Flash player tends to use more than 80% of my resources!

---

### Post by misko_ on 2007-12-31
> **foolsh said:**
> Do you have a swap file?
run 
```
free
```
and see if any exists.
did you install a lot of software lately?
has it always been slow this slow since you installed 7.1?

sasa@Ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        775588     766624       8964          0      36004     414692
-/+ buffers/cache:     315928     459660
Swap:       979924          0     979924

I am using ubuntu regularly since 7.1.

Surfing the web is much solver than on XP at least in my case, and worst example is gmail because I use it a lot, and I am very frustrated when I check my e-mail at home :( , to be honest that is not so bed, because I am on computer all time when I am working.
But now are holiday and it is very frustrated to go on gmail.

---

### Post by misko_ on 2007-12-31
> **stijngysemans said:**
> maybe it is a problem with the flash player.
Flash player tends to use more than 80% of my resources!

I have noticed that Flash player is very hungry for resources, but gmail is also very slow ant there is nothing of flash in gmail...

First weak when I have installed ubuntu, every time when I will go to some site where is youtube video or some video in flash all computer will freeze, but after few days, without my configuration of anything that problem have gone away...

But this one is not...

UPDATE:
I am using Opera for last 2 days, 
it is faster than with FireFox...

---

### Post by motin on 2008-02-04
> **misko_ said:**
> Hello,

First my configuration:
P4 1500 MHz
750 SDRAM
160 GB HDD
ATI RADEON 9600

I use ubuntu 7.10, everything is fine, working normal except when I use Firefox to browse the web. My CPU end up to 100%, and by using top I see that Firefox is responsible. And when I say slow I really mean slow, checking gmail is terrible to open one e-mail take like 2 seconds and to make new label take up to 5 seconds. All this on XP was instant speed.

I have removed trackerd service, because it also was always at 50% of CPU [http://ubuntuforums.org/showthread.php?t=591867&page=2](http://ubuntuforums.org/showthread.php?t=591867&page=2) and I do not even need it...

Why is it so slow ? 
Is it possible that my PC to old ??? Does anybode asle use ubuntu 7.10 on thos configuration and what are his experiencec with browsing the newt ???
Or is is possible that something is not configured correctly ?? 

If you have any idea please put it...

Thanks...

I am experiencing the exact same things for weeks now! Partly because of my intensive use the computer (I lika having everything open and initiating parallell tasks all the time) Now I seem to have more or less solved or at least worked around this. My steps so far have been (Starting of with 1,74ghz single core pentium M, 1gb ram, 74gb HD):

1. Bought more memory - From 1gb to 2gb
This REALLY helped me to get away from swapping and it has been a great boost of my productivity since I no longer have to live through those 20min swap sessions of nothing but trying to quit and save work in order to reboot!

2. Bought a larger hard drive - From 74gb to 234gb
This has finally given me an oppurtunity to not have to spend one third of my computing time freeing up space (or else end up with crashed X sessions and other nasty things when the space on / runs out). And I can now finally fill my media library without having to use and external usb hard drive.

4. Installed [AdBlock]("https://addons.mozilla.org/en-US/firefox/addon/1865") in Firefox
I hoped that this would block most resource intensive flash banners and the likes. It does this in some manner, but overall AdBlock has made it more enjoyable to surf since there is less ads but it block but a small portion of all ads. Still worth the install but didn't solve much performance issues.

5. Switched over to Opera (with inactivated javascript and other plugins) as the default browser
Opera in general - and especially with inactivated javascript and plugins is Formula 1 speed browsing together with great reliability (0 crashes so far). Here I now do all casual surfing, googling, foruming, research and the like - all those uses when all you want is quick and efficent browsing without restrictions of how many tabs could be open at once etc.
This solved the browsing speed issues for these uses - but I still have to use Firefox for watching videos and other sites where plugins (like java) is needed.

6. Made sure Direct Rendering (DRI) was enabled
Since I was using Xinerama to get an extended desktop - DRI was disabled. This makes X use more CPU even when browsing and using the computer as normal. Moving to RandR-based extended desktop enabled DRI and relieves X from many small graphical calculations.
I think this have relieved X from about 10-25 % cpu usage on normal use to under 10% in my case.

7. Installed [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433") in Firefox
I just did this and it seems that this is the final step in my solution of the terribly slow computing problem I have been having. I only use flash for watching videos now and then so it is such a liberty that the other 99% flash instances are not even downloaded unless I tell them to. 

Hopefully I can now fully enjoy both Opera and Firefox based web browsing and computing in general!

Maybe some of my experiences can help you as well. 

Cheers,
Fredrik

---

