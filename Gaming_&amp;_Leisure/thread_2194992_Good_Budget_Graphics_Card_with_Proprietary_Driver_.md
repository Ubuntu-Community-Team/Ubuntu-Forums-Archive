---
title: "Good Budget Graphics Card with Proprietary Driver Support"
date: 2013-12-21
forum: Gaming &amp; Leisure
---

### Post by gerowen on 2013-12-21
I'm running Ubuntu 13.10 64 bit on my HP Pavilion P6803W desktop PC.  After Ubuntu 13.04 I believe, with the upgrade to the newer version of X11, my integrated ATI Radeon HD 4200 is no longer supported by the proprietary drivers package from AMD.  I like to play Steam games on Ubuntu, but the open source drivers do very poorly with this graphics card.  I tried playing Portal, and at 640x480 with all the settings on Low, I was still only getting about 20 fps.

My motherboard has a single PCI Express X16 expansion slot that I could fit a graphics card into.  I'm currently running an AMD Athlon X2 220 dual core @ 2.8 Ghz with 4 GB of RAM.  I'm not planning on trying to run anything terribly brand new, but I'd like to be able to at least play some 3-D games that have something other than flat color textures in full screen mode.

I'm not normally somebody who follows the latest and greatest in the world of graphics cards, so I can read specs all day long and understand technically what they mean, but I don't really know how that would equate to game performance on Linux, and as long as it works well and has proprietary drivers for Ubuntu, I'm game.  I'm looking for suggestions of a good budget video card that could let me do some modest 3-D gaming.  I'm willing to spend up to $100, but I'd like to keep it under $50.

---

### Post by dannyboy79 on 2013-12-21
Nvidia GT 6XX are around $50

AMD HD6XXX are around $50

I personally have an HD7770 Black Edition (around $150 brand new) and am running the latest AMD BETA driver. I can play Metro: Last Light with the graphics slider about half way (the linux version of the game currently can't set AA and other advanced GFX settings).

---

### Post by vanquishedangel on 2013-12-22
Well I favor ati greatly but your milage may vary, for a very basic gameing card that can play HD, the [**Sapphire Radeon HD 6450**]("http://www.ebay.com/sch/i.html?_odkw=Sapphire+ATI+Radeon+HD+6450&_osacat=0&_from=R40&_trksid=p2045573.m570.l1313.TR0.TRC0&_nkw=Sapphire+ATI+Radeon+HD+6450&_sacat=0") with 1 gig ram handled everything for me($55 brand new the day it came out), albeit a bit slow, but good enough in most cases, and the graphics had to be turned down on most games but not completely. For flash gamers it is the best bang for the buck by far. This card works impresivly well considering its cost. This card is perfect for older and low-end computers and no worries about power supply, it runs at 17 watts so it will run with any power supply. Also it wont raise your electric bill. For what this cards main target market was, it is a beast.

I currently have a [**Power color ATI Radeon 7750**]("powercolor ATI Radeon 7750") that cost me about $100, it games well even on newer games with great FPS, so if you are playing higher end games this one will play them on medium to good seetings. This card runs at 78 watts so it should work with most power supplies, but check to be sure. Also you should have a dual core of about 3.0 ghz and 4+ gigs ram to make full use of this card.

On both of these cards I played:

 Heroes of Newerth, [COLOR="#FF0000"]Shaiya[/COLOR], _Neverwinter Nights, [COLOR="#FF0000"]Neverwinter Nights 2 ( GOG version and the gold dvd version)[/COLOR]_, [COLOR="#FF0000"]Fate, Fate 2, Neverwinter Online[/COLOR], 

The red ones are with wine, the others have native clients for linux. The undelined ones can be glitchy sometimes.

On a side note with these cards I had to use the fglrx-updates package.

Also my computers for years have been hp small form factor versions so the cards I can use have to come in low profile versions and be light on power usage due to the limited 200w-240w power supplies. the links are to searches on ebay, no I am not advertising but they have the cheapest usually.

---

### Post by mips on 2013-12-22
I would go for nVidia, better proprietry driver in linux.

I would not get anything lower than a GT640 I reckon.

The Radeon HD 7750 is much better performer though and gives you much more bang for buck, I just worry about the liinux drivers with ati/amd cards, they are not up there with the nvidia ones.

---

### Post by Arthur_D on 2013-12-22
With low requirements you should get a passively cooled card, like a [FONT=arial][SIZE=2][FONT=times new roman]ASUS GeForce GT 630 2GB Silent PhysX[/FONT]
[/SIZE][/FONT]You'll thank me later - no noise at all yet powerful enough for your uses. My brother bought a similar card and it's fine for light 3D gaming - Minecraft runs well with the proprietary drivers and you could probably play more demanding games with the one I mentioned since it has higher specifications.
Around here it costs about 95 USD but you will no doubt be happy with the purchase. :)

---

### Post by dannyboy79 on 2013-12-22
> **mips said:**
> I would go for nVidia, better proprietry driver in linux.

I would not get anything lower than a GT640 I reckon.

The Radeon HD 7750 is much better performer though and gives you much more bang for buck, I just worry about the liinux drivers with ati/amd cards, they are not up there with the nvidia ones.i am actually going to have to disagree with the latest AMD 13.12 driver release. My HD7770 running that driver is working excellent. I actually gained around 8 FPS running Unigine Valley with this latest driver over the previous 13.11 V9.4 driver. Believe it or not I GAINED 40+ FPS on Phoronix Test Suite Team Fortress 2 test, same with Xonotic, and Urban Terror. This new driver is AWESOME and with SteamOS released and currently only Nvidia and Intel GPU's working I am sure AMD is working hard at improving their driver even more so that their new R9 cards work with SteamOS.

---

### Post by oldrocker99 on 2013-12-22
I have a GeForce 650ti (the 650ti Boost came out exactly one week after I installed my 650ti) which cost me $129 a year ago from NewEgg. I have been quite happy with it, both with Windows 7 (which I use only for games) and Linux (where I play most of my games). It appears that nVidia coders are working pretty hard to improve their Linux drivers, so I'll keep using nVidia. I understand that ATI coders are working hard, too, but ATI is far too eager to declare their older chips "legacy."

---

### Post by mips on 2013-12-23
> **dannyboy79 said:**
> i am actually going to have to disagree with the latest AMD 13.12 driver release.

I'm sure it's great but that is one release, historically though things have not been great and tomorrow you could get something not so great. ATI/AMD also have a history of not supporting their gpu ranges/models as long as nvidia does so what works today might end up being obsolete in the not to distant future.

---

### Post by vanquishedangel on 2013-12-25
> **mips said:**
> I'm sure it's great but that is one release, historically though things have not been great and tomorrow you could get something not so great. ATI/AMD also have a history of not supporting their gpu ranges/models as long as nvidia does so what works today might end up being obsolete in the not to distant future.

**That is indeed one downside to ATI**, but on the bright side Ubuntu is always using an old release of fglrx, this leads to longer support in ubuntu. There is also a legacy repo for ubuntu as well that supports older cards (back to the 2xxxx series). Also the opensource drivers are catching up, albiet, a bit slow but for older cards that just dont have the juice anyway to play more advanced games, they work great and perform better in some cases.

So there really isnt much of an issue with that subject as it might seem. I used a Radeon hd 2400 pro for a long time and it played many of the games listed above. My laptop (first computer ever) had an ATI radeon 7500 ( it was from 2001, so no HD) I used that laptop and gamed on it until 2007.

**The other downside is physx**. Nvidia purchased Ageia physx sometime ago (2008) and it is now included in every nvidia graphics card. There are indeed better applications of this type of software available but not backed by a big company like nvidia. Therefore often physx is used in more modern games. The point of ageia physx was to use a separate card to run calculations so the graphics card didnt have to. But now it is on the graphics card for nvidia (kinda defeats the purpose) and nvidia at first was alienating all other graphics cards using this software but were forced to allow physx calculations on the processor. Thus ATI will run games with physx. Not as good as an nvidia card but good enough. Often just disable it or lower the settings if you have issues with it. 

This is similar to microsoft using codecs to cause issues with running progames, or playing movies, or music, in linux. Often the code to run physx on the processor (written by nvidia then implimented in games when they inculude physx) isnt updated and is usually crap code, this gives the impression that other cards arent performing as well, when in truth a lot of that is nvidia's code for physx. Games use physx because when you blow things up it looks cooler.

ATI has its software that nvidia doesnt as well (true form, etc) and also, physx aside, can out perform nvidia in a few departments to. Generally ATI is cheaper than Nvidia in my experience.

This thread isnt about what company is better but rather some info and opinions with facts about graphics cards, so I felt this was relevant to the op.

---

### Post by vanquishedangel on 2013-12-25
Here are some benchmarks for you:

[http://www.sonexpc.com/benchmark/video](http://www.sonexpc.com/benchmark/video)

As you can see Nvidia and ATI are close, but Nvidia releases more graphics cards in a given time frame then ATI and often of the same chip. It also gives info on other graphics cards like intel.

Also many companies use ATI chips and include their own specifications (i.e. Sapphire) and they are not listed in the above website. These cards made by other companies using ATI chips are often at the top of the list for gameing.

---

### Post by mips on 2013-12-25
> **vanquishedangel said:**
> 
ATI has its software that nvidia doesnt as well (true form, etc) and also, physx aside, can out perform nvidia in a few departments to. Generally ATI is cheaper than Nvidia in my experience.

This thread isnt about what company is better but rather some info and opinions with facts about graphics cards, so I felt this was relevant to the op.

If I was gonna use my GPU say 75% for windows games I would get an ATI/AMD GPU. They provide better bang for buck and then there's Mantle for the future which from what I've seen looks really great.

---

