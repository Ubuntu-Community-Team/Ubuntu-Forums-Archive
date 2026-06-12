---
title: "There's definitely something wrong with my gaming performance, and I don't know what"
date: 2017-02-20
forum: Gaming &amp; Leisure
---

### Post by gamelord122 on 2017-02-20
I also posted this on Reddit, but it doesn't seem to be getting much traction over there, so I'll post it here as well:

I've been moving over to Ubuntu full-time in the past few weeks, and I've started to put its gaming performance through its paces.  Hitman was one of my favorite games from last year, and its Linux port is what finally tipped me over the edge to switch to Ubuntu for most of my PC needs.  Unfortunately, there are some issues I'm seeing in Hitman that are indicative of a larger problem.  Here are my symptoms:



[LIST=1]
[*]Hitman hitches every few seconds (like, completely comes to a stop, not just dropping frames).  Between those hitches, it's absolutely running at 60 FPS.  These hitches will sometimes freeze my entire computer, often for several minutes.  I thought it might have to do with the fact that my desktop is a dual monitor setup, so I turned off one monitor and shut down every other program running in the background (Chrome, Messenger for Desktop, Slack, and Discord).  It ran great.  I then turned the second monitor back on.  It still ran great.  I thought it must be because of one of those programs I shut down.  After a reboot, running the game with none of those other programs running, I still got the hitching problem again, so I have no idea what's causing it.
[*]Shadow Tactics: Blades of the Shogun did this as well, including a [visual glitch]("http://i.imgur.com/VtVSK2z.jpg") that their support staff said indicated that I was running on integrated graphics rather than a proper Nvidia card.  My video cables are directly connected to my video card, and there are no other video outputs on my motherboard.  I also confirmed that I was running the latest graphics drivers in the PPA, trying both the 378 and 375 branches.  I switched graphics drivers and rebooted a dozen times while trying to figure out why my performance sucked in this game (no one else was reporting performance problems in Linux, and it ran great at medium settings on my living room Steam Machine).  One of those times, the visual glitch disappeared completely and the game ran flawlessly.  The next time I booted it up, it ran like crap again, and the visual glitches returned.
[*]Empire: Total War's peformance takes a dive from time to time, usually while panning around the map when I have an off-screen unit selected, which is odd.  The performance problems are similar to the above but much, much less severe.  It's possible that the game is so old that I'm just tanking those problems entirely.
[*]Robocraft also had hitching for a few seconds at a time once when I played it in Ubuntu, but it hasn't done it again since then.
[*]Mini Metro and Invisible, Inc. run absolutely fine, but they're not exactly stress tests either...
[/LIST]


The above was run on a machine with an SSD OS drive and a 3 TB secondary HDD.  Both drives are partitioned so that most of it is Windows and some of it is Linux.  I've also got 16 GB of DDR4 RAM, a Core i7 5820k, and a GTX 980 4 GB.  This is a pretty beefy machine for most of these games' standards.


I've also got the privilege of being able to compare this to a brand new laptop, also with Ubuntu 16.10, running off of a single HDD, a Core i7, 16 GB of DDR4 RAM, and a GTX 1060.  The 1060, from the benchmarks I can find, is basically the same performance as a 980.  Hitman runs great on the laptop, with none of these hitching problems (but it does have the visual glitch from Shadow Tactics like the desktop does, with the weird red border around the HUD).


There's got to be something above that might clue you guys in, right?  I don't even know how to troubleshoot from here.  Maybe it's a software issue, maybe it's a hardware issue, but I'm definitely meeting the correct specs to run these games, so something is very wrong.  I guess I want to know what the next step is to diagnose my issue.  Hopefully someone here can help, and I'd really appreciate it.

---

### Post by sgian on 2017-02-21
From this article from phoronix they used the 343.22 driver for the gtx 980 and they didn't notice any problems other than some unsupported features for linux.  [http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx980&num=3](http://www.phoronix.com/scan.php?page=article&item=nvidia_geforce_gtx980&num=3)  Even though it is an older driver, it might be worth a try.  And that ppa you used, are you sure it isn't a development branch?  A development branch will have more bugs than a stable branch.

If it was me, I would purge the ppa, purge the current drivers, and just use the gui in system settings for the recommended proprietary driver.  That is the most likely to be stable.  If nothing else works, I might even try the old 343 driver since the article claimed it worked great.

---

### Post by gamelord122 on 2017-02-21
I have only used the GUI in system settings, but I used it to select the 375+ branches of Nvidia drivers, which are required for Hitman and Shadow Tactics.

---

### Post by sgian on 2017-02-22
Well, since you tried the drivers in the repositories, which are usually older but stable drivers and might not be new enough, there are a couple of options.  
1.  Try the ppa.  These drivers are up to date but often not as proven reliable as the safer repository.
2.  Assuming you are on 16.04, you could try 16.10 which will have newer drivers in its repository.  That might be why it worked better on the 16.10 laptop you saw.  The disadvantage is that 16.10 isn't a long term release, so you will have to keep upgrading every 6-9 months.
3.  Try direct from NVIDIA, which will be more prone to messing up your pc if you make a mistake.

I would recommend the ppa.  Here are some good instructions for the ppa and manual installation methods from a nice guy who hangs out at the Linux Mint forum.  [https://sites.google.com/site/easylinuxtipsproject/12](https://sites.google.com/site/easylinuxtipsproject/12)

---

