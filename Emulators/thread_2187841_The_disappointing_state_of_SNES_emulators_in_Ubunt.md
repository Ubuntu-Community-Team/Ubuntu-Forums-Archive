---
title: "The disappointing state of SNES emulators in Ubuntu 13.10"
date: 2013-11-14
forum: Emulators
---

### Post by caecus314 on 2013-11-14
It's been several years since I ran Ubuntu.  Some of my best college days were spent playing games on ZSNES in Ubuntu against my roommates.  So you can imagine my dismay when I installed 13.10.  ZSNES used to run reliably on 7.10 (!)... but the version in the Saucy repo inevitably crashes after about 15 minutes of gameplay.  See: [http://ubuntuforums.org/showthread.php?t=2159402](http://ubuntuforums.org/showthread.php?t=2159402)

The first thing I tried was installing a different emulator.  Snes9x was always a good option... but apparently it's not in the 13.10 repo yet.  Someone made a package, but it crashes for me whenever I open any menus, so I can't even load a game.  [http://ubuntuforums.org/showthread.php?t=2182196](http://ubuntuforums.org/showthread.php?t=2182196)

So then there's bsnes.  That isn't even an option for a lot of people because the hardware requirements are so high.  Fortunately, I have a new machine that can run it smoothly... most of the time.  Of course, bsnes is what's in the repo, but it's horribly outdated.  bsnes isn't even bsnes anymore.  It's higan.  At least someone made a higan package that is easy to install.  [http://www.playdeb.net/software/higan](http://www.playdeb.net/software/higan)  Unfortunately, even when bsnes is running at a tolerable speed, the user interface and feature set are maddeningly poor.  There's no rewind feature, which I miss dearly.  Fast-forward works... a little--but only if you're syncing to audio using certain combinations of video and audio drivers... and none of those combinations happen to run at an acceptable speed on my system.  Perhaps the most difficult thing to deal with is that pressing ESC doesn't open the menu, and there doesn't seem to be a way to set it to do that.

When everything in the repos failed, I tried compiling my own.  The most recent resources I can find on compiling ZSNES in Ubuntu are from 2007.  No matter how many variations of libraries I've installed, I still can't get it to build.  So next I tried compiling Snes9x.  That worked--but the version I compiled crashes at the same places as the one from the package I downloaded.

Sorry to whine!  I'm just frustrated.  I'm holding onto a fragile thread of hope... that someone will tell me about some option I haven't considered.  I *really* don't want to install Windows on this machine.  That's no fun!  Please help if you can.  Thank you!

---

### Post by BigSilly on 2013-11-14
Yeah it is a bit of a mess at the moment isn't it? I managed to get the [Raring package for Snes9x-gtk]("https://launchpad.net/~bearoso/+archive/ppa") running fine on Kubuntu Saucy 13.10, where it would crash the desktop on regular Ubuntu. I could only put this down to some new bugs in the Unity desktop. I just installed Zsnes (I didn't even know it was still available!), and sure enough even on Kubuntu it doesn't really work.

I think on the modern 64 bit Linux desktop at the moment we are really missing not only SNES emulation, but also Sega Megadrive (+various) too. Kega Fusion is tip-top, but the only version available now is several years old and requires no small amount of manual tweakerage on the users part to get it working. I can get it to work easily, but I imagine many users new to Linux will give it a go, and decide it requires too much faffing with to bother, abandoning it for Windows. :(

---

### Post by caecus314 on 2013-11-14
Thanks for the reply!  At least I know it's not just me.

I could do the old Snes9x package in Kubuntu or Xubuntu--that's something I haven't thought of yet.  It's not quite the same as my preference: ZSNES, but at least it would work!  I'll probably give that a go later this week.

...Unless somebody else has an idea?  Heheh.

---

### Post by BigSilly on 2013-11-15
Managed to get Zsnes to run today on Kubuntu with a command I used years ago for it.

```
zsnes -ad sdl
```

This just changes the audio driver as you probably know, but afterwards it ran fine. It didn't crash the desktop or anything. :)

---

### Post by techzilla2 on 2013-11-21
Just noticed this thread, have a couple considerations about running snes9x, and also wanted to mention a couple things about the SNES state of affairs.

First it appears that there must be something somewhere in the snes9x code, which is choking on a particular unity configuration.  I also would believe this to be the case, as you've also seen the crash after manually compiling.  If the crash happens during menu selection, the problem is likely from a GTK3/WM interaction.   I remember seeing similar menu click crashing on 12.04, running GTK3/Openbox.  I may be able to investigate, but I'm still fairly weak with my C,... and practically illiterate with C++.  I have written a couple small C things, so I can at least generally understand the code.


I also wanted to do a quick breakdown, of the various SNES emulator options, to explain why I promote snes9x.  We have three reasonable choices, ZSNES, BSNES, and Snes9x.  

ZSNES is generally a good emulator, but it's written using a ton of ASM, and is generally unportable.  This is why all the android SNES emulators are often Snes9x rip-offs/forks.  So the emulator itself is decent, but it's future is more questionable.

BSNES, aka Higan, is not my kind of emulator.  Unlike the people who value accuracy, I value something I call playability.  Meaning I'll sacrifice performance right up until things become too slow to play.  Most importantly this doesn't just mean playable on my 8x core opteron workstation..., but playable on a low end PC, and playable on mobile ARM devices.   BSNES isn't close to playable on my Ubuntu ARM chromebook,  that much I know offhand... so how valuable is that accuracy again?  Unfortunately the idiots who write desmume feel the same way, I'm beginning to think 'accuracy' is just the prefered excuse for writing inefficient emulator code.

So what emulator is accurate to play all my games, fast enough to promote 'playability', and portable enough to compile on my Ubuntu ARM chromebook? .... Only one emulator fits this bill, Snes9x!

So I agree completely, the SNES state of affairs isn't ideal, and I wish we could get a clear GPL licence for Snes9x. Simply because it could use as much going for it as possible, and it's most valuable as a full member of this 'community'.  Screw the fanboy's who want to play things 'as accurately as possible', it's not an acceptable trade-off to only play on supercomputers.

---

### Post by General_Faliure on 2014-01-07
I use Zsnes on my arcade cab, (Lubuntu 13.10) it seems to run fine, but i never tried a long playing sesion.
Mednafen also emulates Snes, but i haven't tried it for snes, i use it for Sega Genesis.

---

### Post by LillyDragon on 2014-01-10
The 32-bit package of ZSNES plays without issues under XFCE4, so I wonder what the hangups are on other desktop environments? It's a hacky emulator to begin with, but ZSNES still works under the right conditions.

> **techzilla2 said:**
> BSNES, aka Higan, is not my kind of emulator.  Unlike the people who value accuracy, I value something I call playability.  Meaning I'll sacrifice performance right up until things become too slow to play.  Most importantly this doesn't just mean playable on my 8x core opteron workstation..., but playable on a low end PC, and playable on mobile ARM devices.   BSNES isn't close to playable on my Ubuntu ARM chromebook,  that much I know offhand... so how valuable is that accuracy again?  Unfortunately the idiots who write desmume feel the same way, I'm beginning to think 'accuracy' is just the prefered excuse for writing inefficient emulator code.

How well does "playability" hold up when trying to run games like Earthworm Jim 2, loads of ROM hacks that improve games, and fan-made translations of RPGs? Emulators like ZSNES crash those right off, because it uses dirty hacks and workarounds detrimental to accuracy, all for the sake of speed. You will also notice accuracy problems in games that *do* somehow work. It is outright appauling how bad games like "The Legend of Zelda : A Link to the Past" sound in most emulators, it melts the nostalgia goggles right off of me. BSNES was the first time I truly enjoyed that game on something other than the original system.

Speed was important in the 90's, when most computers had a 100MHz CPU or weaker, but now most machines have multiple processor cores clocked well above 1GHz, and it's more possible than ever to enjoy these games accurately with literal, perfect fidelity to their original platform. I have an average CPU for this time, and can play BSNES just fine; in fact I'm having more trouble getting it to slow down and throttle to 60 FPS.

Accuracy is not an excuse for poor emulation speed, BSNES' code is meant to be as clean as possible, without cheap hacks, so every game will run. It is a controversial emulator for not accepting the disturbingly poor standards of the emulation scene, but ultimately, guess which emulator is still going to be playing the entire SNES library and its rom hacks in the future? Not Snes9x, and most certainly not ZSNES. It is unfair to criticize what you don't understand.

---

### Post by waylonflinn on 2014-05-04
Just a note: BSNES is now called [Higan]("http://byuu.org/higan/").
I had the same frustrating problems with ZSNES (locking up 30 minutes into a game). I thought I'd try Higan. So far, it's the best emulator I've ever used.

---

### Post by adec2 on 2014-05-04
Snes9x-gtk works great for me

---

### Post by ix-jpn on 2014-05-06
I've also experienced the hanging of **zsnes**. This was most unfortunate as I have used it since I was on windows many years ago. It was familiar to use, but the hanging does make it unusable. And it even doesn't print any feedback to the terminal window, so I can't really know what causes the hanging.

**Mednafen** works, but do not get the ancient one (0.8) at the repository. It's 10 years old, get the newer one (0.9) instead, from playdeb (as I did) or compile it yourself. 
Now while mednafen is one of the finest of all emulators, it doesn't have a GUI so it may be scary/unusable for newcomers, but that's why there's ixbar3000 ;) .

---

### Post by adec2 on 2014-05-06
Lets not forget Retroarch that has SNES support too and a damned fine emulator at that. I use retroarch with the retroarch-phoenix gui.
Just a little tricky to set up but once its done you have great emulation for multiple systems

---

### Post by techzilla2 on 2014-06-04
> **johnluke728 said:**
> The 32-bit package of ZSNES plays without issues under XFCE4, so I wonder what the hangups are on other desktop environments? It's a hacky emulator to begin with, but ZSNES still works under the right conditions.



How well does "playability" hold up when trying to run games like Earthworm Jim 2, loads of ROM hacks that improve games, and fan-made translations of RPGs? Emulators like ZSNES crash those right off, because it uses dirty hacks and workarounds detrimental to accuracy, all for the sake of speed. You will also notice accuracy problems in games that *do* somehow work. It is outright appauling how bad games like "The Legend of Zelda : A Link to the Past" sound in most emulators, it melts the nostalgia goggles right off of me. BSNES was the first time I truly enjoyed that game on something other than the original system.

Speed was important in the 90's, when most computers had a 100MHz CPU or weaker, but now most machines have multiple processor cores clocked well above 1GHz, and it's more possible than ever to enjoy these games accurately with literal, perfect fidelity to their original platform. I have an average CPU for this time, and can play BSNES just fine; in fact I'm having more trouble getting it to slow down and throttle to 60 FPS.

Accuracy is not an excuse for poor emulation speed, BSNES' code is meant to be as clean as possible, without cheap hacks, so every game will run. It is a controversial emulator for not accepting the disturbingly poor standards of the emulation scene, but ultimately, guess which emulator is still going to be playing the entire SNES library and its rom hacks in the future? Not Snes9x, and most certainly not ZSNES. It is unfair to criticize what you don't understand.


1. You're arguing against a straw man, I NEVER once advocated anyone using ZSNES. It's heavily written in ASM, which is inherently tied to architecture and platform.  If the choice is ZSNES vs Higan, then you'd be comparing unplayably buggy and unportable to inexcusably CPU heavy ... sure slow beats frozen, but that's still an unacceptable trade-off. Thankfully it's not necessary, times have changed since circa 2003, and while ZSNES is buggy as you remember... Snes9x has improved considerably.

2. Using a modern Snes9x build, I've been able to play EVERY one of my roms without any noticeable bugs.  The codebase isn't full of hacks like ZSNES, I won't deny in the distant past things were not always ideal, but this is completely different emulator than the one you elluded.  To top it off the codebase is portable, IMO the only problem is somewhat 'non-ideal' licensing. 

3. Now to address the ABYSMAL Higan performance, and this applies to EVERY SINGLE PROJECT FROM THAT CODE BASE. (hopefully not forever, but still very true as of 2014)   Back in the 90's we did have 100MHZ systems, yea you're right, so writing everything in unportable unmaintainable ASM was the only option (ZSNES).  You're also right today things are thankfully much better, and your statements about specs are true for DESKTOP systems.   Thankfully we don't need to choose from unmaintainable code vs. IMO proudly wasteful CPU usage... and that's how those devs see it I've read their comments and priorities.

 It's one thing to say, hey we don't need ugly hacks anymore... I agree. Or to say we don't need to write in ASM,... I agree. 
 Both come at the unreasonable cost of portability or maintainability. 

This is where things go very wrong for the Higan team, and their line of thinking..... They simply think this means you don't need to think about performance period, they think they can run a non-optimized architecture because performance doesn't matter anymore.... they think that properly utilizing the GPU is optional, let alone those multiple CPU cores.  Simply stated, their lack of values reflect their project. 

If they took their commitment to accuracy, and combined it with an EQUAL commitment to performance, then I'd likely be running their code now.  This doesn't mean shortcuts, this means a deeply considered architectural design that allows full resource exploitation. I know from reading both their code and their developer comments, that this isn't their priority.  Instead of committing to as much performance as possible, they opt for an easier to maintain codebase.... this has NOTHING to do with the accuracy, and it's a BS excuse that is believed by people don't get down and dirty in their methodology.  

Why do they keep bringing up hacks?  Because it's a strawman argument to mislead people into believing they did everything sans hacks.... but they didn't, and this is true on EVERY single architectural consideration.  They didn't even come close either, they didn't even do ALMOST everything unless it made things insanely complicated...  They may have felt that way, but that's because why complicate things for something you don't care about!

---

### Post by byuu on 2014-08-13
> There's no rewind feature (in higan), which I miss dearly.

If you're willing to build bsnes v070 (available at code.google.com/p/bsnes/downloads/list?can=1), that version has rewind support, and a much friendlier GUI. It's a bit older, but it still holds up well.

> Perhaps the most difficult thing to deal with is that pressing ESC doesn't open the menu

I've never heard of anyone doing that on a standard UI. Use the F10 key to do this, as with other GTK applications. In higan, escape is mapped to release mouse capture used by light gun emulation.

> Snes9x has improved considerably.

Indeed, Snes9X v1.54 is quite good. Unfortunately it's been in beta for over three years now, and earlier versions have audio processor issues.
But if you can track down one of the betas, I'd highly recommend it.

> Using a modern Snes9x build, I've been able to play EVERY one of my roms without any noticeable bugs.

The key word you use there is "my roms".

Can you play SD Gundam GX? Hayazashi Nidan Morita Shougi (1 or 2)? Speedy Gonzales beyond level 6-2?

I could point out noticeable minor rendering issues in Air Strike Patrol, Dai Kaijuu Monogatari 2, NHL '94, Mega Man X2/X3, and so on. But those are indeed petty. I could do the same for games that run a bit too fast or slow, or sound a bit off.

The important thing for you is that *you* don't notice any issues in the titles *you* play. Which is great. You clearly have no reason to use a slower emulator with less features and a clunkier interface.

But other people may play different games than you. And they may have different values than you about what is acceptable. To each their own.

> Thankfully we don't need to choose from unmaintainable code vs. IMO  proudly wasteful CPU usage... and that's how those devs see it I've read  their comments and priorities.

Whom are these other devs you speak of? Because I am the only developer working on higan, and that has always been the case.

> They simply think this means you don't need to think about performance  period, they think they can run a non-optimized architecture because  performance doesn't matter anymore....

Some of the smartest minds in emulation have helped optimize the code in higan/bsnes. Exophase (gPSP, Drastic), Cydrak (dasShiny), blargg (QuickNES), etc. I routinely profile the code and optimize hot spots. I've even created alternate versions of each processor core optimized to run faster at the expense of accuracy. The fastest one can maintain 80fps on a first-gen Intel Atom netbook I bought in 2008. Although that is still 80% slower than the latest Snes9X release, it also emulates more details of the system.

But yes, I sacrifice performance for code maintainability frequently. Instead of maintaining elaborate and fragile state machines, I use a cooperative threading model that sometimes comes at a performance penalty for no actual gain. The code is meant to serve as informal documentation on how the hardware works.

I also emulate many complex behaviors that zero commercial games rely on, which slow things down more. Because my goal is to emulate hardware, not software. The latter is a beneficial consequence of the former.

With Snes9X, your argument is that you haven't seen any bugs in the handful of games you play. But that's easily disproven by my examples.
With higan, my argument is that there are currently no known bugs. Multiple people have tested every single game in the entire library to verify that. It's also not perfect, a bug pops up every six months or so, and I fix it.

A large part of the reason I was able to get higan so accurate and bug-free, is *because* of that emphasis on code cleanliness, even if it meant sacrificing some performance. I simply couldn't have gotten where I was today if the codebase were harder to understand and reason about.

> they think that properly  utilizing the GPU is optional, let alone those multiple CPU cores.

I have the most advanced multi-pass pixel shader system of any emulator at the moment, tied with what RetroArch is doing in that space.
We do complex CRT simulations, curvature, edge cleaning, etc all in the GPU.
But that is for post-processing effects.

If you think that an SNES emulator should utilize the GPU, or multiple CPU cores, for the base machine emulation, then well ... I mean no disrespect, but you really shouldn't comment on matters you do not understand. No SNES emulator does either of these things, and for very good reason.

Now, emulators for much higher-frequency systems with 3D graphics? Sure, they make a lot of sense there for speeding things up. Although they do often require sacrifices, they can at times be quite necessary given the constraints of modern processing power.

> If they took their commitment to accuracy, and combined it with an EQUAL commitment to performance

Accuracy and performance are mutually exclusive. It's okay if you disagree, a lot of emulator developers disagree with me on this point, too.

But accuracy gains almost inevitably sacrifice performance, unless the code is of very poor quality in the first place.
This of course is not a dismissal to wave off poorly written code, but I don't think my code is poorly written.

Look, you don't seem to care about extreme attention to emulation detail, and that's fine. Few people do.
But you need to understand something: for the people who do, higan/bsnes is very roughly ten times as precise as Snes9X is, despite being anywhere from 2x to 5x slower, depending on the options you compile with.
There are exponentially increasing CPU demands for accuracy, combined with exponentially decreasing visible advantages for doing it.

Snes9X really is already in the best possible position as a compromise between the two extremes that will serve the most users. There wasn't much sense in me writing another Snes9X clone when they already filled that market niche beautifully.

If you don't care about perfection, if you want more features, if you care about battery life, use Snes9X.
If you have the processing power and value correctness above all else, use higan.

One isn't universally better than the other. They both have their use cases, and their user bases.

> I know from reading both their code and their developer comments, that this isn't their priority.

Correct, performance is not my priority. But I also don't wantonly waste CPU resources. Everything I do is for a good reason.

Since you state you've reviewed my code, can you please point out some of your most egregious examples? I'll be happy to shed some light on the rationale for each of them.

> Why do they keep bringing up hacks?

Because others keep insisting that higan has to be compared to Snes9X and ZSNES.

Because people such as yourself keep making comments like, "I've been able to play EVERY one of my roms without any noticeable bugs." If I had a dollar for every time I've heard someone say that "ZSNES is perfect" ...

Because people call into question my intelligence, my integrity, my ethics, my values, and so forth. So I have to constantly keep explaining myself, like I am doing right now.

I really don't have any interest in getting people to use my emulator. I only release it publicly for the people who want it.
It's cost me ten years of my life, and I've spent over $20,000 buying carts just to verify and map their board layouts.
And in return, I have made exactly $0 from it in sales.

I don't want fame, I don't want power, I don't want money. I just want to preserve a system I really enjoy, and have fun doing it.

> to mislead people into believing they did everything sans hacks.... but they didn't

I will grant you that my other emulators are immature, but what hacks am I currently using in my SNES emulation?

---

### Post by adec2 on 2014-08-15
Byuu your emulator for snes is fantastic, thanks

---

### Post by michael-piziak on 2014-11-18
ZSNES was working fine for me except that I couldn't configure the diagonal directions to work with my 2 Gravis Gamepad Pro controllers - which makes all games useless if you can only move in 4 directions - north south east and west.

Now I'm using Snes9x.  It seems to be working good thus far - but I'm running Ubuntu 12.04 lts.   I used the 3 terminal code lines to install it.

[B][SIZE=3][FONT=verdana]sudo add-apt-repository ppa:bearoso/ppa[/FONT][/SIZE]
[/B][COLOR=#333333][FONT=Verdana][SIZE=3]**sudo apt-get update**[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana][SIZE=3]**sudo apt-get install snes9x-gtk**[/SIZE][/FONT][/COLOR]


[COLOR=#333333][FONT=Verdana][SIZE=3]This came from the website: [http://www.upubuntu.com/2012/09/a-list-of-best-game-console-emulators.html](http://www.upubuntu.com/2012/09/a-list-of-best-game-console-emulators.html)

[/SIZE][/FONT][/COLOR]Update:  I installed Ubuntu 14.04 lts on my sisters computer.  It can't run Snes9x or ZSNES without freezing.  For some reason, my computer that has 12.04 lts will run Snes9x, but again not ZSNES because the diagonal directions won't work right on the gamepad.   So yes, there is a lack of SNES emulation, especially since 14.04 lts won't support SNES emualtion.


Note:  I'm running 12.04 32 bit on an Intel Core 2 Duo
Update:  I'm now running 12.04 64 bit on the same computer and Snes9x still works.

---

