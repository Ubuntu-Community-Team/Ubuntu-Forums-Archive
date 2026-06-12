---
title: "Discussion: A distro for Games to push Linux into the mainstream public."
date: 2009-01-02
forum: Gaming &amp; Leisure
---

### Post by Anacardo on 2009-01-02
A few thoughts I had in my mind for quite some time. I'll be brief.

1) Games have always been one of the differentiating factors of Windows when compared both to Macos and linux. To the general, uninformed user, Windows DO games (apart from a lot of other things) others do not. Games has also always been a good showcase for the platform running it. Games are important for a widespread adoption of any operating system. Period.

2) Microsoft screwed up, badly. It committed to the console market, negletting one of the most important windows selling points. Of course we might say that they merely followed the trend of the software houses which are basically doing the same, still the fact remains. Regardless of the direct X 10 and the new unified "experience" (Windows live, now needed by some games like GTAIV), windows VISTA SUCKS at playing games. And it does suck because unless you use a plain vanilla system, whenever you had a normally configured one the framerates simply begin to drop. And it's not only that, of course the interface is crewed as well, being cumbersome, overly complicated, and heavy. Add to this the fact that most games need patches and new drivers right from the start (happened to me with fallout 3 and farcry2) and you get the point.

3) the last generation of Consoles have somewhat been a slight disappointment. Surely they're doing strong in terms of sales and such (no big surprise here since there's basically no alternative), but there are a lot of videogamers complayining.

3) PC gaming needs a new approach. More streamlined and lightweight, with a dedicated and simpler interface that works on large monitors and TV screens, with a new system to deploy games and play them.

4) Microsoft will never develop such a thing. It's simply against their own interests. It's a very good time to do something like this.

What I am thinking:

A lightweight distro. Just for games. No frills attached.
Three ways of deployment: 
 a)Live, that sits in the game media. You insert the DVD/CD/USB key? whatever in you pc, boot, play and that's it. No installs.
 b)Installed as a dualboot with whatever os you might want. Needed for buying/downloading/installing games from the net. Separate from your windows os or even your linux distro. Clean, small, secure and simple.
 c)As a windows and Linux launcher. (slower than the native mode)

Streamlined:
Very few running services. Only the necessary things to run games (or even a single specific game). No clipboard, advanced Plug and play support, indexing, samba, or other fancy stuff. It has to be lightweight, fast and stable. The fewer things it does, the better.

Easy to use:
Very little configuration needed. No file manager, Nothing. Only a good looking interface to configure the most basic aspects of the environment, to launch games and, eventually, to download or update content from the net. The use of the mouse shouldn't be necessary. No windows nor icons. Think of a streamlined and cleaned PS3 or WMC interface.

Stable:
Self contained applications. Basically each game comes with all the files and it needs to run. Apart from the basic stuff, it will be the game developers to choose if they need to add more funcionality to the system or not. To some extent, they might even provide different versions of the same shared libs found in the main system, so that, provided that the core stuff hasn't changed, a game might continue working even if you've updated your system to a new, incompatible version. Installing and uninstalling games (in the non live versions) would become unpainful, easy and quick. No patches, no beta drivers to download that crash other games. Every game is by itself. To some extent, the ideal thing would be to have every game as a indipendent system within it's own, with just a shared centralized bootloader/agent that updates the single games when needed, provides the basic interface funcionality and manages keep the consistency across the system.

It would probably attract: 
the hardcoregamers willing to get the latest frame rate in a particular game. By being really streamlined, it would mean that very little would get in the way.
The casual gamer (windows or linux user) who doesn't want to mess up with his system and install games that eat his own hd space, corrupt the system with securom stuff, rootkits or other bloatware. Update and patch things only to discover he just screwed his own Blueray player with a non-signed driver.
People with older systems and hardware. No more finding out that a game needs windows VISTA, direct xzy, 20GB of hd space and you're stuck with xp. The game COMES with the system and all the stuff that it needs. 
What do you  think?

---

### Post by eragon100 on 2009-01-02
[http://live.linux-gamers.net/](http://live.linux-gamers.net/)

[www.xeiso.com](www.xeiso.com)

---

### Post by Anacardo on 2009-01-02
> **eragon100 said:**
> [http://live.linux-gamers.net/](http://live.linux-gamers.net/)

[www.xeiso.com](www.xeiso.com)

WOOOOOOOPS.... Sorry for that.. :( Good to hear that somebody though of it. Wow, it's almost exactly what I was thinking about...

---

### Post by sad_iq on 2009-01-02
Sorry to bring the "bad" news...but it's allready done...[http://live.linux-gamers.net/](http://live.linux-gamers.net/) offers a live DvD distro based on archlinux packed with some nice games, videodrivers for Ati and Nvidia(probably more)...and some other things. You should try it out and see if you like it :)
    The only thing that Linux needs to go "mainstream" in the gaming industry, and probably the only thing keeping Microsoft still on the lead in the Desktop market share is "Direct X", and as long as Microsoft keeps it Closed-Source Linux will never get ahead or even near it :(
    Unfortunately OpenGl is still ages behind directX, and soon game developers will lean twards creating directx only games(but let's hope I'm wrong on this one ).

---

### Post by eragon100 on 2009-01-02
> **Anacardo said:**
> WOOOOOOOPS.... Sorry for that.. :( Good to hear that somebody though of it. Wow, it's almost exactly what I was thinking about...

The live DVD is a nice project, but it has one major problem: Even tough they release new version regularly, the game versions on the cd are often not the latest available, and sometimes, old and new version aren't network compatible. (openarena for example, on the DVD it's 0.8.0, while 0.8.1 has been out for about 2 months now. The next version of the DVD will offcourse include 0.8.1, but that will likely get outdated as well. Same goes for almost all the other games on the disk.) :(

For commercial games the problem would be that if you made an update you would have to let your users download a 700 MB or a few GB large iso image instead of a 10 mb or something update, and it would cost the user a blank cd/dvd, as well. :(

---

### Post by eragon100 on 2009-01-02
> **sad_iq said:**
> Sorry to bring the "bad" news...but it's allready done...[http://live.linux-gamers.net/](http://live.linux-gamers.net/) offers a live DvD distro based on archlinux packed with some nice games, videodrivers for Ati and Nvidia(probably more)...and some other things. You should try it out and see if you like it :)
    The only thing that Linux needs to go "mainstream" in the gaming industry, and probably the only thing keeping Microsoft still on the lead in the Desktop market share is "Direct X", and as long as Microsoft keeps it Closed-Source Linux will never get ahead or even near it :(
    Unfortunately OpenGl is still ages behind directX, and soon game developers will lean twards creating directx only games(but let's hope I'm wrong on this one ).

I have read somewhere that EA plans to release mac versions of all their titles in the future at the same time they release windows versions.
Unless they use cider, they will **have** to use opengl for that. :wink:

---

### Post by Vadi on 2009-01-02
Silliest idea *ever*. I don't dualboot to play Windows games, and I surely won't be rebooting to play a linux game.

---

### Post by compiledkernel on 2009-01-02
I tend to aggree with you on the Dualboot issue Vadi. 

Speaking from a purist perspective, I think rallying behind the already existing game communities will bring linux gaming to the light. No need for a game specific distro, but there is need for support of those who make titles for native linux.

---

### Post by Anacardo on 2009-01-02
> **Vadi said:**
> Silliest idea *ever*. I don't dualboot to play Windows games, and I surely won't be rebooting to play a linux game.

I do, especially when running windows. My usual system won't handle any game, considering the load of crapware I have to run. A casual gamer won't probably do that  since he wouldn't probably game on the pc (today the REAL casualgamer is usually somebody who comes home from the office, turns on the tv, finds nothing and then pops up a game in his console, to play for half an hour or so). 
An hardcore gamer usually does that, beacause he wants the most from his hardware and of course because when he plays... he plays. For hours. No nee dfor anything else than keyb and mouse (or joypad) 
Anyway here's another heresy: I believe the only way for the Linux gaming world to gain momentum is to get a killer app. Sadly enough, due to the obvious portability strenghts of Open Software, I believe Linux gaming would kick off thanks to a closed source game that really sells and it's not easly ported to other platforms. Exactly the way Msoft and Sony are doing on their own respective consoles with exclusive titles like Gears of war 2, little big planet and Metal Gear.
As for the need of a gaming distro... I think there's definitely the need of one. (of course there's the need of games as well lol) and why is that? simple: Windows has become too much bloated to play games on a reasonable manner and the only OS that can be streamlined and used as a foundation for such a system is Linux. The direct X dilemma is very problematic. Direct X (at least the 9) is probably the best piece of technology that microsoft possesses. But to me it's not really the pivotal point. You can do a great game with very limited technology, it's just a matter of finding a good concept with good history, characters and playability and throwing a lot of good art and clever tricks into it. Think of Hal life2, it's technologically years behind Crysis and yet does anybody think is a lesser game? COD 5 sometimes looks really bad on screen. Who cares with te tons of stuff you're thrown at and the good cinematic moments? Yes maybe the linux games are lagging behind due the technology, but I also believe the faults might be found elsewhere (not that it's anyone's fault. Games nowadays are multimillion dollar ventures...with hundreds of talented and paid professionals behind each title)

---

### Post by jpeddicord on 2009-01-02
Hehe, referrer stat tracking tipped me off to this thread. :P

> **Vadi said:**
> Silliest idea *ever*. I don't dualboot to play Windows games, and I surely won't be rebooting to play a linux game.

> **compiledkernel said:**
> I tend to aggree with you on the Dualboot issue Vadi. 

Speaking from a purist perspective, I think rallying behind the already existing game communities will bring linux gaming to the light. No need for a game specific distro, but there is need for support of those who make titles for native linux.

I sort of agree. Rebooting into a full-blown game distro just for a little while is inefficient and a little annoying. It's one of the reasons that there will always be a version of Xeiso (linked earlier in thread) that runs right on your existing Ubuntu install.

There are use cases for a live gaming distro, such as when on a PC that isn't yours, you are Windows user who can't play Linux games, or for setting up public kiosk systems. The biggest case would probably be a dedicated MythTV-like console. An ambitious goal, but it's not too far off.

---

### Post by Vadi on 2009-01-03
> **jacobmp92 said:**
> I sort of agree. Rebooting into a full-blown game distro just for a little while is inefficient and a little annoying. It's one of the reasons that there will always be a version of Xeiso (linked earlier in thread) that runs right on your existing Ubuntu install.

Good stuff.

tip: [https://wiki.ubuntu.com/AptUrl](https://wiki.ubuntu.com/AptUrl) for the download page ;)

---

### Post by jpeddicord on 2009-01-03
> **Vadi said:**
> Good stuff.

tip: [https://wiki.ubuntu.com/AptUrl](https://wiki.ubuntu.com/AptUrl) for the download page ;)

Yeah, I'm doing that now on some not-yet-live wiki pages on the site via pkgb.net, but the repository still needs to be added manually.

---

### Post by Vadi on 2009-01-03
That it does, but the package can be installed like that after :)

---

