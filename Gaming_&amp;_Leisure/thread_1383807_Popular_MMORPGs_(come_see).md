---
title: "Popular MMORPGs (come see)"
date: 2010-01-17
forum: Gaming &amp; Leisure
---

### Post by Haxx2010 on 2010-01-17
Hey Guys, Here again asking for your opinions on MMORPGs that work well with WINE or that are just native to Linux... I am running Ubuntu9.04 Jaunty.

I have looked around but most seem poor in GFX, I am looking for a game with reasonable gfx, or just a game with a great community...

I used to play Flyff, WoW and Lineage2 so I'm pretty open minded :>

---

### Post by steve3279 on 2010-01-18
World of Warcraft runs great with Wine.  I currently play it just fine.  There is a page on wowwiki.com dedicated to making WoW run with Wine.  Also I think the latest patch required some sort of Visual C++ library.  I did a Google search on it and downloaded the fix in a few minutes... Play WoW on Linux!

---

### Post by Naegling23 on 2010-01-18
guild wars and world of warcraft are both platinum rated on wine (they run flawlessly).  Dungeons and dragons online also runs well in wine, I think it takes a performance hit though, and you need to run a custom launcher to get the game installed and running, but it runs though (see the wine appdb, or search the wine section of these forums)...

Wow - huge community, great game, monthly fee.

Guild wars - no monthly fee, not a true MMO (thats not a negative though), still a large community, but not on wow's scale.

D&D online - completely free, but with payed content that may, or may not unbalance the game.

---

### Post by steve3279 on 2010-01-18
I believe that Eve-online will also work with Wine, although I haven't gotten it to run successfully.

---

### Post by konqueror7 on 2010-01-18
rf online has a great gameplay, though gets you grinding after lvl40...try a private server...:D

also, bloodymare is also okay...

---

### Post by MaximB on 2010-01-18
Regnum Online has a NATIVE 32 and 64 bit Linux clients, and it's free to play.

---

### Post by m0nt3 on 2010-01-18
[LEFT]eve runs great on wine. it has a very good user support base in the eve forums:
[http://www.eveonline.com/ingameboard.asp?a=channel&channelID=630463](http://www.eveonline.com/ingameboard.asp?a=channel&channelID=630463)

and here is an excellent ubuntu specific howto for getting eve started.
[http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1226117](http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1226117)

i highly recommend it for anyone tired of swinging a sword or casting a spell. 
[/LEFT]

---

### Post by thumpszilla on 2010-01-18
Eternal lands has a native client, great community, pvp has dedicated areas, free to play, and there is even a linux guild. Graphics are not the greatest but still a great game with very low systen requirements.

---

### Post by AllRadioisDead on 2010-01-18
Eternal lands has brutal graphics.
[IMG]http://www.gameogre.com/reviewdirectory/upload/Eternal%20Lands.jpg[/IMG]

---

### Post by handy on 2010-01-19
I installed Regnum on my Arch box today, which is running the ATi open-source packages, which unfortunately were not enough for me to be able to play Regnum. :(


[I]Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version[/I]


I'm in the process of installing Eternal Lands at the moment, though I'm not expecting a positive result, again due to the new OS ATi drivers.

---

### Post by proxess on 2010-01-19
> **handy said:**
> I installed Regnum on my Arch box today, which is running the ATi open-source packages, which unfortunately were not enough for me to be able to play Regnum. :(


[I]Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version[/I]


I'm in the process of installing Eternal Lands at the moment, though I'm not expecting a positive result, again due to the new OS ATi drivers.

There are some work-arounds for that, plus some deb packages, tho I don't specifically remember. I found them, tho was unsuccessful at running the game. It loaded, but then I got seg-faulted on the game loading screen. I could run it in fail-safe mode but the graphics were broken. I could try again tho...

---

### Post by handy on 2010-01-19
> **proxess said:**
> There are some work-arounds for that, plus some deb packages, tho I don't specifically remember. I found them, tho was unsuccessful at running the game. It loaded, but then I got seg-faulted on the game loading screen. I could run it in fail-safe mode but the graphics were broken. I could try again tho...

Thanks for your reply. :)

I guess I'll take it to their forum & see what the story is.  I do think that if I was running Catalyst, it would very likely work.

I really don't want to use Catalyst though, I'm so over its unreliability, & for Arch I have to downgrade xorg-server to 1.6 because Catalyst is still not compatible with the versions released since!

---

### Post by proxess on 2010-01-19
I'm in a worse ship than you. My GPU isn't supported anymore (as of xserver 1.5 and catalyst 9.2), so I have no choice.Catalyst has good 3D and bad 2D. FOSS drivers are in the opposite situation. Right now 3D is more important tho 2D has to obviously work 100% (due to un-evolving GUIs, desktops)really making ATi users groan. True, nVidia doesn't release GPU specs, but their drivers work...

---

### Post by handy on 2010-01-19
I expect that inside of 6 months, my HD2600Pro will be flying in both 2D/3D, using the *stable* open-source solution.

People are getting greatly improved 2D/3D speeds, right now using the .git packages & the right version of the kernel.

The stable release of kernel .33 & the related packages mesa et al, are going to bring big improvements, & now that the Evergreen tech' info' has been released by AMD, the current GPUs are going to start to see support also, though I don't know how quickly the dev' team is working on that branch.

All good. :)

Hopefully your GPU will get open-source support too?

---

### Post by proxess on 2010-01-19
I certainly hope so. I've got a x2300 (not HD), which is pretty much a 'forgotten' GPU.

Does Lucid have the latest builds?

---

### Post by handy on 2010-01-19
> **proxess said:**
> I certainly hope so. I've got a x2300 (not HD), which is pretty much a 'forgotten' GPU.

Does Lucid have the latest builds?

It is in the R600 series, the same as mine.  It should already be able to do great 2D, & slow 3D, as in World of Goo plays perfectly, but more complex 3D games don't/won't.

The Arch guys playing with .git & the like are getting terrific results in 2D/3D speed with R600/R700, but still bugs exist.

---

### Post by proxess on 2010-01-20
> **handy said:**
> It is in the R600 series, the same as mine.  It should already be able to do great 2D, & slow 3D, as in World of Goo plays perfectly, but more complex 3D games don't/won't.

The Arch guys playing with .git & the like are getting terrific results in 2D/3D speed with R600/R700, but still bugs exist.

It's not. It's in truth a re-branded x1400 or x1600 (can't remember which), but seeing that it has a different ID from the old card, it's usually forgotten. It's pretty strange actually.

Heck, even google earth crashed X on these drivers.

---

### Post by handy on 2010-01-20
> **proxess said:**
> It's not. It's in truth a re-branded x1400 or x1600 (can't remember which), but seeing that it has a different ID from the old card, it's usually forgotten. It's pretty strange actually.

Heck, even google earth crashed X on these drivers.

So, the open-source driver progress shown in the following link is not having any effect for you yet?

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

---

### Post by proxess on 2010-01-20
I'll try installing Lucid in a few days (IMHO don't really like 9.10) and give a more recent release a go.

Another thing I hate is *OpenGL Video Rendering* flickering on *Compiz*. This didn't happen with the old FGLRX drivers. Pleast don't tell me to use other renders (software like Xv or X11) as they are all horrible.

The x2300 is an RV500 card.

---

### Post by handy on 2010-01-20
> **proxess said:**
> I'll try installing Lucid in a few days (IMHO don't really like 9.10) and give a more recent release a go.

Another thing I hate is *OpenGL Video Rendering* flickering on *Compiz*. This didn't happen with the old FGLRX drivers. Pleast don't tell me to use other renders (software like Xv or X11) as they are all horrible.

The x2300 is an RV500 card.

I never use Compiz, so I don't have experience in that area.

Using Ubuntu stable packages will slow down the speed with which you will be able to experience the improvements in the kernel, mesa (& associated) & xf86-video-ati.

Though you can certainly rest assured, you will experience as the Ubuntu releases roll on, the benefits of the OS dev' teams work on the ATi GPUs, which is moving at an incredibly fast rate, mainly thanks to the releases of the technical documentation by AMD.

If you want to move outside of the stable Ubuntu packages there is some good info' in the following linked to thread.

The first post is worth a read, as I try to keep it up to date as best I can, if you check out the links in the Ubuntu section, it goes into detail about using the more up to date packages re. the open-source ATi support:

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

---

### Post by proxess on 2010-01-21
I installed Lucid x64 minimal plus Xubuntu desktop yesterday. I had this weird problem while logging in, so I deleted and re-created the user. I'll check out performance later on.

---

### Post by camillejane on 2010-01-22
WOW and Runescape for me...
been play it for a while and really enjoyed it...
I just don't if others would agree to me..
btw, I'm camillejane, anewbie in here...

---

### Post by handy on 2010-01-24
> **camillejane said:**
> WOW and Runescape for me...
been play it for a while and really enjoyed it...
I just don't if others would agree to me..
btw, I'm camillejane, anewbie in here...

Welcome to the forum, I hope you enjoy your time here.:)

---

### Post by proxess on 2010-01-25
Ok moved to Lucid, had quite a battle to get things running.

Regnum still won't work unfortunately. But... 3D support for my GPU is just so so so awesome! Compiz, OpenGL Rendered Video in VLC and Google Earth all running at the same time, no flickering, no crashing, all very very smooth!!!

---

### Post by personjerry on 2010-01-25
Haven't read thread but just giving my opinion:

Savage, Savage 2 (I recommend highly) free native RPG/RTS game with sick graphics.

Planeshift

The Mana World (2d though)

these are all native.

---

### Post by Allwynd on 2010-01-26
im currently playing Runescape ([http://www.runescape.com/](http://www.runescape.com/))
its java based, you probably know it, in summer 2009 i registered, cuz it seemed cool, but i logged in and i saw the graphics and underestimated it, now i started it and its awesome
back then i was with windows 7, now im with ubuntu 9.04 and i cant use the HQ, cuz it crashed my whole ubuntu session :D :D :D

im trying ou cabal online.. it may work, maybe it wont

---

### Post by wolfyking2 on 2010-01-29
There is a nice MMORPG called Dofus.  It is free, but you should pay if you want the 'full package.'  Download the 2.0 version, and my ingame name is Qras-Fury or Home-Dizzle.  Have fun ^^

---

