---
title: "I want to Build a Linux Steam Console"
date: 2013-05-27
forum: Gaming &amp; Leisure
---

### Post by Consolist on 2013-05-27
It's time for this project now I think .
Specs should be something similar to PS4 , but the good thing is it can be upgraded later and not set to look like a stupid Microsoft/Sony box :) 
Then I'ts just sit back and enjoy the steam evolution :)

Anyone have made something similar?

---

### Post by Consolist on 2013-05-27
What kind of obstacles will I run into do you think ?

---

### Post by Consolist on 2013-05-27
Any comments from design to software/hardware is welcome .

I want to have all details planned before I get to it.

I was thinking of maybe building it in plexi or glass too rather than trying to make it melt in .
Have a LOT of crazy ideas also for it so guess in the end it will boil down to something reasonable.

---

### Post by efflandt on 2013-05-27
It is not rocket science, just so it has a good multi-core cpu, decent video (nvidia works well), and enough RAM. Even though Steam is still 32-bit, for certain games a 64-bit OS and 8 GB RAM may help to cache disk access for some games that end up huge (after playing TF2 my system is caching 4.9 GB).

The only issue I ran into is that my Linux partition was previously only 100 GB, so with virtualbox and other things on my system I started running short on space when Team Fortress 2 was installing (10 GB I think) and later when it redownloaded and shuffled files to a different location for current Steampipe file arrangement. Since my hard drive started going bad, I shrunk Win7 and expanded Linux to 250 GB on the new drive. If things go totally wrong at some point your games and stats are stored on the Steam Cloud, so all you have to do is install Steam (on any OS) and once everything downloads, everything will be there.

I have had no Linux specific issues running Steam since late beta in January, just little, sometimes general (any OS), glitches that get resolved in the next Steam or game update (automatic).

---

### Post by CatKiller on 2013-05-27
If you're going for a dinky case you'll need to make sure that the graphics card you choose will actually fit. If it's going in an enclosed space you'll need to consider cooling; you don't want it to run loud but you don't want it to run too hot, either. The same sorts of considerations that you'll find for people building an HTPC will apply.

You also won't necessarily need it to be a graphical powerhouse, either. My 560 Ti runs everything that's currently available for Steam on Linux with no problems at my desktop resolution and TV resolutions are even lower.

---

### Post by Consolist on 2013-05-27
Ok , No heat will not be an issue , It's not going to be passive cooled or in a small HTPC-case or something like that .
I want it cooled by a few 120 fans so I can run them slow an super silent somehow. I have a few fans and they are cheap also.

Ok the games on steam do not need a lot of power yet .
Do you know what is the most demanding game at the moment ?

Maybe I try to build it for what is needed now instead of futureproof it for the next big FPS .
I like nice looking 2d games , like Outland ,Deadlight and Trials the most anyway.

---

### Post by Consolist on 2013-05-27
I checked the specs on some games and it looks like I can get by with an AMD phenom for 95$
and a radeon 7750 and 4gb ram.
That can be upgraded later if needed. 

processor :
AMD Phenom II X4 965 Black Edition Deneb 3.4GHz Socket AM3 125W Quad-Core Processor HDZ965FBGMBOX

---

### Post by King Dude on 2013-05-27
For CPU, I suggest a non-APU (since graphics drivers for AMD and Linux are crummy) AMD chip, or... sigh... an Intel chip with embedded graphics. Look, I really did not like Intel, but I recently discovered that its graphics hardware works better with Linux. However, if you're on a tight budget, go for the AMD CPU.

For graphics card, I recommend either Nvidia or Intel. Again, Intel has crappy video cards, but they work better with Linux.

The rest of the hardware you can go bananas with. But I also suggest getting a small, 10-40GB SSD for the Operating System. SSDs ran via PCIe 2.0 are about three times faster than Hard Drives that run via SATA 6GB/s.

---

### Post by Consolist on 2013-05-27
Oh, I did actually consider amd 
a-10 and maybe adding a 7750 later . 
I do not know why really but I want amd cpu and gpu , and I do not care that much if it is the best performance in the world as long as it is working.
As far as AMD a-10 and Linux I am pretty confident the linux community do sort it out .
They always do.

---

### Post by oldrocker99 on 2013-05-27
What is the most demanding game at the moment?

I started out with my budget desktop with a low-end DX 11 Radeon, which I upgraded quickly, dismayed at the fglrx drivers for Linux for ATI, to a low-end nVidia 520, which was certainly better (imho, nVidia supports Linux far better than ATI, no matter what Linus says). I recently upgraded my video card to a 650ti (of course, the 650ti Boost came out 2 weeks after I installed it...). The biggst difference I saw in Linux Steam games was in Trine 2, which had been unplayable on the 520, and runs smoothly on the 650ti. Also, the main menu for Crusader Kings 2 stuttered as the map perspective changed; it doesn't now.

I would say Trine 2. Even Serious Sam for Linux had been playable on the 520, and it's certainly graphically-intensive.

---

### Post by King Dude on 2013-05-27
Yeah, AMD drivers do not work half of the time, and when it does work it works like crap. But the CPUs, especially the FX-series, are golden, mostly because they do not require drivers. So your best bet would probably be an AMD CPU with an Nvidia video card. And remember, two low-mid ranged cards in SLI may turn out to be more powerful and less expensive than a single upper mid ranged card.

---

### Post by King Dude on 2013-05-27
Check out these.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819113284&IsVirtualParent=1](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113284&IsVirtualParent=1)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121714](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121714)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227709](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227709)

---

### Post by Consolist on 2013-05-28
According to AMDs website they have linux-drivers in beta .

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx)

I have no doubt in that you are totally correct about AMD graphic.

My experience with linux is that things do work later rather than sooner , and then it works.
I have no rush doing this project.

---

### Post by cRaZyBisCuiT on 2013-05-28
If you have a price limit and some more details in what you wish (max. noise, performance etc.) I could build you up an example shopping card. My advice would be using an Intel i3 + nVidia graphics card (660ti e.g.). + 8 GB ram. If you want to build that kind of console in +1year maybe an AMD APU may be a better solution then (cheaper, less hot, less noise etc.). Right now the drivers are not that good.

---

### Post by King Dude on 2013-05-28
> **Consolist said:**
> According to AMDs website they have linux-drivers in beta .

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-3LINBetaDriver.aspx)

I have no doubt in that you are totally correct about AMD graphic.

My experience with linux is that things do work later rather than sooner , and then it works.
I have no rush doing this project.
I've tried them with my AMD video card. My whole system was screwed up afterwards.

> **cRaZyBisCuiT said:**
> If you have a price limit and some more details in what you wish (max. noise, performance etc.) I could build you up an example shopping card. My advice would be using an Intel i3 + nVidia graphics card (660ti e.g.). + 8 GB ram. If you want to build that kind of console in +1year maybe an AMD APU may be a better solution then (cheaper, less hot, less noise etc.). Right now the drivers are not that good.
Intel CPUs are more expensive for less power. For example, a six-core Core i7-3970X Extreme Edition is 3.5Ghz (4.0Ghz turbo) with a 6 x 256KB L2 cache and a 15MB L3 cache is $1039.99, whereas an eight-core AMD FX-8350 is 4.0Ghz (4.2Ghz turbo) with a 4 x 2MB L2 cache and an 8MB L3 cache is $199.99.
Sources:[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16819113284"]
http://www.newegg.com/Product/Product.aspx?Item=N82E16819113284[/URL]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116877](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116877)

---

### Post by Consolist on 2013-05-28
Amd drivers are a big dissapointment so skip that, still in beta is not good enough .

I want to build it cheap and upgradable at first since I guess most games will be indie titles a year or two .

Blizzard will release a new WOW or something but they keep it as a secret so I rather spend the cash on games than hardware for futureproofing , I do not play WOW anyway.

Trine 2 is now the height of the bar so to speak , and I have not played it yet so it is a nice one.

As far as specs go I want it to be upgradable but as smart as can be at the moment.

SSD can wait , I have a harddrive.

The cheapest processor on same socket as AMD's better ones is Sempron 145 , and can be unlocked to dual core .
Would it be enough ?

---

### Post by King Dude on 2013-05-28
What's your budget? I recommend an AMD Phenom II X4 965 Black Edition, which is $94.99 on NewEgg. It's inexpensive, reliable, and still has enough power to handle all of the modern games. Even if you do not play games, you'll still get at least five years of use out of it.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103727)

I had one of these, and I can personally say it's one of the finest processors I've ever bought.

---

### Post by Mikeb85 on 2013-05-29
> **Consolist said:**
> It's time for this project now I think .
Specs should be something similar to PS4 , but the good thing is it can be upgraded later and not set to look like a stupid Microsoft/Sony box :) 
Then I'ts just sit back and enjoy the steam evolution :)

Anyone have made something similar?

For PS4 like specs, you'd want a fairly top end processor (but doesn't have to be the absolute best), and the best Nvidia graphics card you're willing to purchase.  8 gigs of RAM should be good (RAM is cheap nowadays), and an Xbox 360 controller.  

[http://www.makeuseof.com/tag/connect-your-xbox-360-controller-to-your-linux-gaming-rig/](http://www.makeuseof.com/tag/connect-your-xbox-360-controller-to-your-linux-gaming-rig/)

Oh yeah, also might be a good idea to build a minimal Linux distro, and have it boot right into Steam.

---

### Post by Consolist on 2013-05-29
Budget is not huge for this , then I guess an XBOX one is a better choice because Microsoft buy the good Xbox Live titles and make them xbox exclusive.
Well that is a good reason to buy it and not to buy it, I guess.

I do want it upgradeable though , thats what I hated most with microsofts 360,  the fan started to sound like an airplane and dvd-laser sucked, guess it's something they make so you do have to buy a new console after 3 years.
They make everything in their consoles crap cause they want it to last no more than five years.

To change the fan or the dvd would be overpriced or ban the xbox . I rather play awesomenauts and Trine 2 and halflife 2 or whatever than have to support that company  every month just to buy their exclusive XBLA games .

Budget is somewhere around 200$ for processor and graphics card. 

The phenom and 650 seems to be a good choice . The 650 is not sli though so maybe then a Motherboard with single Pci-e is the way to go. Or 650 ti boost with sli and sempron .

---

### Post by Consolist on 2013-05-29
> **Mikeb85 said:**
> For PS4 like specs, you'd want a fairly top end processor (but doesn't have to be the absolute best), and the best Nvidia graphics card you're willing to purchase. 8 gigs of RAM should be good (RAM is cheap nowadays), and an Xbox 360 controller. 


[http://www.makeuseof.com/tag/connect-your-xbox-360-controller-to-your-linux-gaming-rig/](http://www.makeuseof.com/tag/connect-your-xbox-360-controller-to-your-linux-gaming-rig/)


Oh yeah, also might be a good idea to build a minimal Linux distro, and have it boot right into Steam.


Guess so , but then I would have a system that is overkill in the beginning , and insufficient in the end of the lifecycle and total crap after .
It would be totally stupid to get that just for booting into steam with the games in it instead of buying a PS4 .

---

### Post by Consolist on 2013-05-29
Yes , Xbox controller is great . 
Great that it works on Linux !

Do you know if there is some nice linux distro for htpc and steam ?

---

### Post by Mikeb85 on 2013-05-29
> **Consolist said:**
> Yes , Xbox controller is great . 
Great that it works on Linux !

Do you know if there is some nice linux distro for htpc and steam ?

Pretty much any distro will work as a base for that purpose.  SUSE Studio is an online tool that makes building OS images very easy, you can customize your distro any way you want (using SUSE tools of course).  Arch, Debian or Gentoo would work great, as they're fairly minimal and you can customize.  Even something like Lubuntu would work well, or you could get a minimal Ubuntu installation and modify that (I haven't personally played with any Ubuntu installs other than the basic Unity desktop though).

---

### Post by Consolist on 2013-05-29
Found this and it seems like the A10 apu works good with linux .
It can be good to know , and some credit to AMD for it they should have .

[http://www.phoronix.com/scan.php?page=article&item=amd_a10_5800k&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_a10_5800k&num=1)

Cash/Performance this have to be one of the best .

---

### Post by whatthefunk on 2013-05-29
I would seriously consider a small ssd for the OS to go on.  It really speeds things up.  I have a small 60 GB drive for the /root and /home and store all my data on a regular harddrive.  The sdd was the best investment I ever made computer wise.

---

### Post by King Dude on 2013-05-29
> **whatthefunk said:**
> I would seriously consider a small ssd for the OS to go on.  It really speeds things up.  I have a small 60 GB drive for the /root and /home and store all my data on a regular harddrive.  The sdd was the best investment I ever made computer wise.
Beat you to it. He said that he'd buy an SSD later down the road.

> **Consolist said:**
> Found this and it seems like the A10 apu works good with linux .
It can be good to know , and some credit to AMD for it they should have .

[http://www.phoronix.com/scan.php?page=article&item=amd_a10_5800k&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_a10_5800k&num=1)

Cash/Performance this have to be one of the best .
I don't recommend it, not with Ubuntu anyways. You'll need AMD's propriety drivers *AND* an AMD video card to take full advantage of the APU, and I think it's a mistake to use either of those things with Linux.

> **Mikeb85 said:**
> Pretty much any distro will work as a base for that purpose. SUSE Studio is an online tool that makes building OS images very easy, you can customize your distro any way you want (using SUSE tools of course). Arch, Debian or Gentoo would work great, as they're fairly minimal and you can customize. Even something like Lubuntu would work well, or you could get a minimal Ubuntu installation and modify that (I haven't personally played with any Ubuntu installs other than the basic Unity desktop though).
Minimalistic versions of Ubuntu are not going to have as much of a positive effect on a 3.2Ghz CPU, 8GB RAM machine as a 1.5Ghz CPU, 2GB RAM machine.

---

### Post by Mikeb85 on 2013-05-29
> **King Dude said:**
> 
Minimalistic versions of Ubuntu are not going to have as much of a positive effect on a 3.2Ghz CPU, 8GB RAM machine as a 1.5Ghz CPU, 2GB RAM machine.

No, they won't, but he did clarify that he'll start with modest specs.  Besides, you can build a minimal HTPC or Steam Box with a few clicks on [http://susestudio.com/](http://susestudio.com/)

If you can, why not?  I agree it's not necessary though...

---

### Post by Consolist on 2013-05-29
> **King Dude said:**
> Beat you to it. He said that he'd buy an SSD later down the road.


I don't recommend it, not with Ubuntu anyways. You'll need AMD's propriety drivers *AND* an AMD video card to take full advantage of the APU, and I think it's a mistake to use either of those things with Linux.


Minimalistic versions of Ubuntu are not going to have as much of a positive effect on a 3.2Ghz CPU, 8GB RAM machine as a 1.5Ghz CPU, 2GB RAM machine.

The best would be if it would autostart a HTPC frontend like XBMC , something made for the xbox controller , I guess it is a minor issue , but still I thought someone knew the easiest option.

LXDE is supernice but maybe not for the 360-Controller.

A reason to have the OS lightweight could be to use the copy=toram , thats a real good thing, at least it was before ssd , so yes SSD will be faster but a few seconds wake up time for the HD is not a dealbreaker.

If a-10 + 2x HD7750 is supported for Linux , it would be a good step by step build I think.
If not the a-10 and 650 ti boost is still a good setup/upgrade.

---

### Post by Mikeb85 on 2013-05-29
Another option hardware-wise is an Intel Ivy Bridge CPU with HD 4000 graphics.  It's powerful enough to run TF2, most indy games, even 0 A.D. runs fairly well on my laptop with HD 4000.  You can get an i3 3225 chip with HD 4000 for $150, the motherboard for $100 or slightly less, and you can get a discrete Nvidia card in the future when you upgrade.  They're very capable CPUs and GPUs.

---

### Post by King Dude on 2013-05-29
> **Mikeb85 said:**
> No, they won't, but he did clarify that he'll start with modest specs.  Besides, you can build a minimal HTPC or Steam Box with a few clicks on [http://susestudio.com/](http://susestudio.com/)

If you can, why not?  I agree it's not necessary though...
Define what your idea of a "modest" computer is. To run most of the modern and future Steam games you'd need at least a dual core processor clocked at 3.0Ghz and 2-4GB of DDR2 RAM. To take advantage of the minimalistic nature of Lubuntu, Xubuntu, and Kubuntu you'd need no more than a dual core processor clocked at only 2.33Ghz, and that's enough to run maybe Team Fortress 2 and Half-Life 2, but that's about it.

> **Consolist said:**
> The best would be if it would autostart a HTPC frontend like XBMC , something made for the xbox controller , I guess it is a minor issue , but still I thought someone knew the easiest option.

XBMC as of my knowledge currently lacks the ability to execute Steam games. But development is going on to integrate emulators inside XBMC by way of RetroArch.

> **Mikeb85 said:**
> Another option hardware-wise is an Intel Ivy Bridge CPU with HD 4000 graphics. It's powerful enough to run TF2, most indy games, even 0 A.D. runs fairly well on my laptop with HD 4000. You can get an i3 3225 chip with HD 4000 for $150, the motherboard for $100 or slightly less, and you can get a discrete Nvidia card in the future when you upgrade. They're very capable CPUs and GPUs.
Buying an Intel processor will bite him in the butt later down the road when he wants to upgrade because even though the i3s and i5s are inexpensive, the i7s run a small fortune on the market. He's much better off with an AMD CPU, as they are inexpensive yet powerful.

---

### Post by Dlambert on 2013-05-29
> **Consolist said:**
> Yes , Xbox controller is great . 
Great that it works on Linux !

Do you know if there is some nice linux distro for htpc and steam ?

Not with steam it doesn't.

---

### Post by agingerturtwig on 2013-05-29
If you want to stick to AMD make sure to get something Piledriver based like the 6300 or the 8320.

---

### Post by Consolist on 2013-05-30
> **Dlambert said:**
> Not with steam it doesn't.

Sorry , but this do not help me much .

Steam do support the xbox controller . Both wireless and with wire .

Please guys if you have some experience , share it .

---

### Post by cRaZyBisCuiT on 2013-05-30
What you can do is to build a script for XBMC to start Steam im BigPictureMode and close XBMC ... that means you can controll xbmc and steam with a controller. That Script could also launch XBMC once you close Steam. XBMC could be adjusted to boot straight into it's ui.

---

### Post by Dlambert on 2013-05-30
> **Consolist said:**
> Sorry , but this do not help me much .

Steam do support the xbox controller . Both wireless and with wire .

Please guys if you have some experience , share it .

Sorry. To clarify: Yes, Linux has built in drivers for the 360 controller. However, when trying to play source games on steam (portal/left4dead2) the controls are messed up/not working. 

There is the alternative Xboxdrv, but I couldn't get that functioning either.

---

### Post by Consolist on 2013-05-31
Ok everything seem to be a bit of trouble , guess it will take some time until it's just download a distro - install to usb with unetbootin - put it in the steam console and enjoy.

---

