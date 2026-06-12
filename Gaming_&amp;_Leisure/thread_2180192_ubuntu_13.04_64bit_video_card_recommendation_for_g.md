---
title: "ubuntu 13.04 64bit video card recommendation for gaming"
date: 2013-10-11
forum: Gaming &amp; Leisure
---

### Post by Josh_Taneja on 2013-10-11
Hi

Looking for inputs on recommended video cards for playing 3D games in Ubuntu 13.04 64bit Intel (older computer ~ 2008) 

- PCI Express 2.0 support  ( Radeon HD 5450 needs PCI express 2.1)
- Affordable price ~ $50 range
- Low profile and lightweight (unlike the Radeon HD 4870)
- Not needing special PCI Express power supply.

Currently using Radeon x1300, but it has practically no 3D support in Ubuntu 13.04 and glxf3d drivers did not work either without corrupting the desktop.

Thanks in advance.

---

### Post by DanglingPointer on 2013-10-12
If you are gearing up for the avalanche of games starting to hit Linux due to Steam's push, then you will need a beastier card preferably from Nvidia's range due to their better propriety drivers.  $50 range isn't going to cut it unfortunately for those games coming out.

From my experience; I've got a 5870 at the moment and I am already struggling with Wargame Euro Escalation and Wargame Airland Battle (two awesome RTSs!)  The source engine games run well on the highest detail, 16x AF on 1080p with no AA. They do stutter at the beginning of each level on L4D2 though.  HFL2 and all episodes run well with everything maxed out!  I haven't tried TMF2 and Portal on Linux yet but I played them using the 5870 on high settings on Windows a couple of years ago.
I played Raven - Legacy of a Master Thief on low settings for chapters 2-3. They were not playable on medium or high settings!
I'm currently playing ARMA Tactics with all eye candy turned on.  Not many options to bump it up though.
I'm likely to buy The book of Unwritten Tales next.

I briefly had a GTX260 which I swapped out for the 5870.  At that brief time the GTX260 played better than the 5870 even though the 5870 is a lot more powerful.  I blame the driver for this.
I can only conclude that I need a current Nvidia 7 card to play with better or best settings with the best games on offer now and those that are definitely in the pipeline due to Steam.

Thus I recommend you save more money and wait till November as the price of all graphics cards are up in the air at the moment due to AMD's new R7 and R9 releases.  
Nvidia has already dropped prices for some of their cards.  
R9 290x will be released on Oct 15 and if the performance matches the Titan then you can expect a possible significant price drop for the 780 and Titan.  Possibly even the 770.

All PCIE's are backwards compatible.  PCIE 2.0 will do just find with a 3.0 card.  You can always just upgrade the mobo, chip and ram later on.  That is what I did with the 5870, I bought it when I used to run a Core 2 Quad Q9650 on a PCIE 1.0 board!  the 5870 is a 2.0 card.  I upgraded the system a couple of years ago and now it is running on a PCIE 2.0 board.  I'm probably going to do the same now when the Titan drops in price.  Plug it into this aging board then 2yrs from now get another board with PCIE 3.0.

---

### Post by Arthur_D on 2013-10-12
> **Josh_Taneja said:**
> Hi

Looking for inputs on recommended video cards for playing 3D games in Ubuntu 13.04 64bit Intel (older computer ~ 2008) 

- PCI Express 2.0 support  ( Radeon HD 5450 needs PCI express 2.1)

Depends on the brand; XFX and Sapphire both have 2.0 as requirement - though as DanglingPointer pointed out it should scale nicely down anyway.
But don't expect triple-A titles to work well for 50$ - should be okay for some light gaming though.

---

### Post by Josh_Taneja on 2013-10-15
Does anyone remember the days of ATI Rage Pro 3D and early Radeon back in year 2000-02? I remember playing games like Need For Speed (Hot Pursuit), Tomb Raider,  Spiderman in resolutions of 1600x1200 on Windows 98 using DirectX and 3D acceleration was pretty good on those legacy cards. 
Then came Radeon X1300 and X1600 around 2005-06. I am guessing the hardware on X1600 was at least 5x or 10x better than the RagePro3D days. So they do have plenty of potential as far as hardware is concerned. Then what happened is Ubuntu 11.04 and later dropped 3D support for these newer X1300 legacy cards... (bummer).

I am guessing its a problem with the 3D driver development for Linux did not progress properly, either from ATI/AMD side or Ubuntu side. Is it the same issue with other Linux Distros (like Fedora)? etc. i.e. no 3D support for ATI Radeon cards from 2005-06 ?

Are there any other affordable low profile 3D cards out there which are supported in Ubuntu 12.04 (and later versions) for lightweight gaming?

---

### Post by mastablasta on 2013-10-15
are PCI 2.1 not backwards compatible with PCI 2.0

i know SATA plugs are, USB plugs as well as AGP ports were compatible. i had 8x AGP card on 4X AGP slot. it's just a bottle neck but not unsupported. same as USB - you can use USB 3.0 disk on USB 1.1 only data tranfer will be slower.

also it depends what kind of games you want to play.

---

### Post by oldrocker99 on 2013-10-21
> **Josh_Taneja said:**
> Does anyone remember the days of ATI Rage Pro 3D and early Radeon back in year 2000-02? I remember playing games like Need For Speed (Hot Pursuit), Tomb Raider,  Spiderman in resolutions of 1600x1200 on Windows 98 using DirectX and 3D acceleration was pretty good on those legacy cards. 
Then came Radeon X1300 and X1600 around 2005-06. I am guessing the hardware on X1600 was at least 5x or 10x better than the RagePro3D days. So they do have plenty of potential as far as hardware is concerned. Then what happened is Ubuntu 11.04 and later dropped 3D support for these newer X1300 legacy cards... (bummer).

I am guessing its a problem with the 3D driver development for Linux did not progress properly, either from ATI/AMD side or Ubuntu side. Is it the same issue with other Linux Distros (like Fedora)? etc. i.e. no 3D support for ATI Radeon cards from 2005-06 ?

Are there any other affordable low profile 3D cards out there which are supported in Ubuntu 12.04 (and later versions) for lightweight gaming?

The AMD/ATI cards which use open source drivers use them since AMD/ATI declared those cards "legacy" and quit supporting them directly. In their defense, they have worked with the open source driver devs, making what had been proprietary information available to the devs.

Nonetheless, this is why I, when I upgraded my video card, chose nVidia.

---

### Post by Kevin_Arnold on 2013-10-21
I'd go nvidia but all of your requirements sound like you're not really looking for a gaming card at all. $50 and low profile is basically the exact opposite of a gaming card. Anyway, if you're just looking for passable 3D, just pick up any nvidia card that matches your budget.

---

### Post by Ranko Kohime on 2013-10-21
> **Josh_Taneja said:**
> PCI Express 2.0 support  ( Radeon HD 5450 needs PCI express 2.1)
I have a 2.0 motherboard, and I'm running a 7850.  They're backwards compatible, and to the best of my knowledge, only the beastliest cards are pushing the bandwidth limit of 2.0 right now.

> **Josh_Taneja said:**
> Affordable price ~ $50 range
Depends on what games you plan on playing in the future, $50 might not be enough.

> **Josh_Taneja said:**
> Low profile and lightweight (unlike the Radeon HD 4870)
It's a desktop, how lightweight does it really need to be?  (as for low-profile, small case?)

> **Josh_Taneja said:**
> Not needing special PCI Express power supply.
Almost all cards come with an adapter to connect the card to the Molex connectors that you doubtlessly have at least one spare of.

---

### Post by mastablasta on 2013-10-22
actually i have old radeon 3650 HD (it is now considered legacy in linux... :-( ). anyway i have it on XP mashcine. I play mostly a bit older games and some latest ones. Ofcourse the latest ones are nto the most graphially intensive (e.g. Kerbal Space programme, Hearts of iron, i bet Skyrim could also run, minecraft...). But a bit older ones run great. Unreal Tournament 2004, BF2, Civilization 4, Rome total war, Doom3, Stalker series... 
I was trying to get a newer one, but i've noticed there is not much power gain in that price region i was looking for. So i've dropped it for now. This one has a bad fan, so maybe i will pick up somehting when it falls off...

I also have Radeon 9600 XT on Linux box. works great. haven't been gaming much wiht it lately, but i do know i can run Oblivion on medium on Windows XP, plays a number of older games well (Morrowind on max if i remember correctly). My point is even with these old cards one can play a game or two. maybe it wont' run BF4, but then neither will linux :-P

---

### Post by dannyboy79 on 2013-10-22
i picked up an Nvidia 8400GS for very cheap on newegg and am fairly happy with it's performance based on the price. It meets all your requirements I believe

---

### Post by oldrocker99 on 2013-10-22
I bought a NvIDIA 650Ti and am very satisfied with its performance. Of course, one week after I installed it, the 650 Ti Boost was announced. Such is life.

---

