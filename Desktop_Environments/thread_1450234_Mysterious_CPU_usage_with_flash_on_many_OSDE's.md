---
title: "Mysterious CPU usage with flash on many OS/DE's"
date: 2010-04-08
forum: Desktop Environments
---

### Post by Lord.Quackstar on 2010-04-08
After trying to convert to linux from Windows XP, I've ran into a bunch of problems.

Specs:
Box: Dell Dimension 3000
OS: (currently) Lubuntu 10.04 Beta 1 (LXDE)
Processor: Pentium 4 2.7 GHz
RAM: 256 MB <--- big killer
HD: 7200 RPM IDE over 2 disks
Swap: Swap partition on current disk, swap file on ntfs on other disk

So here's my problem: Flash is killing this computer. What I mean is that certain flash video's that play extreamly well in Firefox in XP with ~80% processor usage, use 100% cpu and lag like crap in CHROME (also tested in Firefox, same result)! Because I thought it was my OS or desktop environment, I've used Linux Mint XFCE, Fluxbox, and LXDE as well; Xubuntu, then LXDE as after install; and now Lubuntu; all with the same result. All have been pretty fresh installs. In each OS/DE, I've used Google Chrome, Chromium, and Firefox. All yield ridiculous processor usage, and most of the time the video is unwatchable. HOWEVER, currently in Lubutu I've sucessfully been able to watch this flash video at an acceptable framerate. But when I try and play a flash game right next to it, framerate drops to barely acceptable and CPU shoots up. This I have been able to do for a year successfully in XP. Note that all browsers had either AdThwart (chrome) or AdBlock Plus (firefox). This shouldn't make speed worse because their removing resource consuming flash ads.

What confuses me is that on an older laptop (lesser processor but more RAM), I am able to play this video AND play a flash game at the same time, both with better than acceptable framerates (CPU bounces from 100% to 90%).

One other question I have is why flash in Linux is so buggy/slow? My fan is worn out and therefor sounds like a jet engine when under heavy load. XP was fine, but just watching the video makes it spin up and therefor very loud. 

I know this isn't a limitation of my hardware, as I've said many times XP has handled this well. Is it a limitation of Flash in linux? Is it a limitation of browsers in Linux? Or is my configuration of Ubuntu wrong?

---

### Post by lovinglinux on 2010-04-08
> **Lord.Quackstar said:**
> I know this isn't a limitation of my hardware, as I've said many times XP has handled this well. Is it a limitation of Flash in linux? Is it a limitation of browsers in Linux? Or is my configuration of Ubuntu wrong?

It's a limitation of flash on Linux. I was able to solve my problem only after upgrading my CPU from a P4 single core to a Core2 Duo, but flash still uses 40% of my CPU.

Anyway, see the Flash Optimization section of my [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by tgalati4 on 2010-04-08
On windows, I think flash can use the DirectX extensions to speed up video.  In Linux, flash is strickly software rendering--no hardware acceleration.  So yes, either dual-core or watch your stuttery video while your cpu melts.

Because flash is closed-source, it will always suck on linux.  Hopefully HTML5 will take over for a better linux multimedia experience.

---

### Post by soltanis on 2010-04-09
Yeah, Flash sucks.

You can try stripping down your system even more, but that might not help. Firefox on Linux tends to not be so great, actually, and I've personally found love in Google Chrome; the little anything search bar and the pretty slim memory profile are encouraging, so I'd give it a try on your system and see if you get any performance improvements, however minimal.

Also, I'm not familiar with LXDE, or if Lubuntu comes with Pulseaudio, but that application seriously is not fit for usage on low spec computers (or any computer in my opinion but that's a different matter), but I would check to see if you have it installed, and if you do, remove it. It could be your sound playback actually slowing you down.

---

### Post by jrusso2 on 2010-04-09
What do you want you only got 256 mb of ram you using up the ram and having to use swap which is slow.

---

