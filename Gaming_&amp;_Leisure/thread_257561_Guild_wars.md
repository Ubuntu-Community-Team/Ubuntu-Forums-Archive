---
title: "Guild wars?"
date: 2006-09-14
forum: Gaming &amp; Leisure
---

### Post by DiJEH on 2006-09-14
Has anyone had any real luck at running Guild wars on Wine? It's honestly the only reason I'm still using windows right now :)

---

### Post by aswells on 2006-09-14
I would also be interested in hearing people's opinions on this. I knew a person a while ago that had ventrilo and guild wars running in wine, so I know it is possible.

---

### Post by erk on 2006-09-14
There is a few threads on this already. Basically Guild Wars will load and run under wine under edgy with the latest wine package on my IBM Thinkpad R52. There is a serious problem with the 32 bit mouse cursor GW uses being invisible. The fix is ether patch wine to make it recognise the rgba cursor, or turn on X transperancy, it's not really easy, see the winehq site for details. You should make sure that Wine is working with other games, sound etc. before tinkering with GW. Also the -dx8 flag should be used with GW as the directX 9 support is not too flash in wine. Lots of RAM is required, at least 1GB for smooth sailing.

---

### Post by Sentinel83 on 2006-09-15
I am in the same situation where GW is a large reason why I can't make the final jump.  I tried doing the install with the latest wine, and I can get the installer to connect to ArenaNet and start to work.  But, it crashes a few seconds into the install.  I've followed as many posts as possible, but I've resigned for now.  
Hopefully, someone has some luck...:confused:

---

### Post by erk on 2006-09-15
> **Sentinel83 said:**
> I am in the same situation where GW is a large reason why I can't make the final jump.  I tried doing the install with the latest wine, and I can get the installer to connect to ArenaNet and start to work.  But, it crashes a few seconds into the install.  I've followed as many posts as possible, but I've resigned for now.  
Hopefully, someone has some luck...:confused:

Have you tested your wine installation with other games yet? It's important to get the Wine config right before looking at GW. Wine's config varies with hardware.

---

### Post by ATAQ on 2006-09-16
Hey Guild wars is officially supported on cedega, it says it on [http://transgaming.org/gamesdb/games/view.mhtml?game_id=3370](http://transgaming.org/gamesdb/games/view.mhtml?game_id=3370)

---

### Post by oly on 2006-09-16
it is also very easy to set up with cedega, i have been playing it for some time in ubuntu dapper, the pointer issue might fix itself if you right click a few times, or it does in cedega because it starts of invisible untill you click a few times for some reason.

---

### Post by handy on 2006-09-16
There are a lot of GW player's dual booting, or like me, running it via Cedega, who are hanging out for the news to come through that Wine has done it...

---

### Post by FyreBrand on 2006-09-24
How well does it run under Cedega?  I am thinking of shelling out the $15 for 3 months to try it out, but I'm not sure it will even run alright.

My system:
P4 3Ghz HT
1GB Ram
ATI Radeon X300(PCIX) 128MB

My system doesn't have a hard time running it in Windows, but the X300 isn't a very burly video card.  Depending on the area in game my FPS ranges from 25 - 35.  Do you lose framerate under Cedega?

This is the only game I own that requires Windows.  Everything else, like NWN and Planescape: Torment, run under wine or natively.  Man I really wish this would work in wine.

---

### Post by Perfect Storm on 2006-09-25
The only problem I can see with your rig is your ATI card. That can course it won't work.


Other than that your specs are good. I have ran GW with
P4 2.4 Ghz 1024 mb ram gf 6600 GT 256 MB
in high details under Cedega.

---

### Post by chameleon_789 on 2006-09-25
I tried GW with Cedega with all sorts of settings on a previous Ubuntu install.. when it worked, it would work for 3-4mins then crash, with the fonts messing up.  Just thought I'd mention that before you shell out :|

Can't remember what version of Cedega or kernel, but I think it was because I had an AGP card (Geforce 6600 GT 128mb)

---

### Post by handy on 2006-09-26
Try the [Cedega_demo]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Simulation/Cedega-9843.shtml") first?

---

### Post by FyreBrand on 2006-09-26
Thanks for the feedback.  I will try out the demo.  It would be really convenient if I could get it running.  That would open up a whole partition for me.  Sometimes I feel silly leaving a 40GB Windows partition for the sole purpose of playing Guild Wars.  The Nightfall chapter looks nice, but I'm not buying it if I have to play it in Windows.

---

### Post by handy on 2006-09-26
> **FyreBrand said:**
> Thanks for the feedback.  I will try out the demo.  It would be really convenient if I could get it running.  That would open up a whole partition for me.  Sometimes I feel silly leaving a 40GB Windows partition for the sole purpose of playing Guild Wars.  The Nightfall chapter looks nice, but I'm not buying it if I have to play it in Windows.

You should know that the demo is not the latest version, & the latest version of Cedega does have some improvements re: pre-configuration for a lot of games.

I only use Cedega to play GW, so I can't say how well it does or doesn't work with other games?

**[Edit:] *I believe that Transgaming has improved it's support of ATI in a very recent update of Cedega...***

---

### Post by embedded_ on 2006-11-03
cedega is crashing on me...
i am not running edgy...never tried ubuntu yet...gentoo worka great so far...
i have tried with ati radeon 9200 (open source and latest ati closed source as of around late oct 2006 with no luck)...please do not hold out any hope for linux/ati support unless amd flexes on them.....
nvidia rules for gpu......
installed nvidia card and was on  beryl in less than 2 hours....
still trying to tweak wine.....
works for gw yet seems to need patch for 32bit cursor...and for better performance
cedega crashes with nvidia.beta.drivers for beryl  says video card not supported...

[email]msals1@netzero.com[/email]

---

### Post by FyreBrand on 2006-11-03
There is another thread about compiling wine with the 2 mouse patches.  It works, but not great.  I can only play in 1024x768 (it won't display other sizes even if I configure it to).

It works good enough for me though.

I don't have that crappy ATI card anymore I bought an XFX Geforce 6800XT.  I love it.  It works great and did I mention I love the nvidia card? :D

Here is the link to: [**"How I got Guild Wars to Work in Wine"**]("http://www.ubuntuforums.org/showthread.php?t=283122").
Here is the link about CFLAG switch when compiling wine (in Edgy) to avoid segmentation-faults:  [**"Wine 0.9.24 Compiling => Segmentation fault: Possible solution"**]("http://www.ubuntuforums.org/showthread.php?t=287986")

---

### Post by Knark on 2009-01-03
Makes me feel lucky...i just installed it and it worked! I use ubuntu intrepid with wine 1.1.5. As long as i maximize the window everything runs smoothly, i just can't minimize the window but that's no problem for me.

---

### Post by Bios Element on 2009-01-03
GW with Wine works perfectly with a few reg edits. Just do your homework and it should run fine.

---

