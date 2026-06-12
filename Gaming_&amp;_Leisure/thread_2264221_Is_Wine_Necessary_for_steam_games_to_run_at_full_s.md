---
title: "Is Wine Necessary for steam games to run at full speed?"
date: 2015-02-06
forum: Gaming &amp; Leisure
---

### Post by mandarpowale on 2015-02-06
Is wine necessary as I plan to play DOTA 2 and Left 4 Dead 2 on my PC, 
(I am dual booting UBUNTU 12.04 LTS with Windows XP SP3 32 bit)

My system specifications are as follows
================================
Amd Athlon II X2 260 3.2 GHZ
Asus M4N68-T LE-V2
4GB DDR III 1333MHZ GSKILL RAM
ASUS HD7750 1GD5 V2
1 TB WD PURPLE
500 GB WD GREEN
(C: WINDOWS XPSP3 250 GB , E: UBUNTU 25GB '/', 16 GB 'SWAP', 226GB '/home' F:463 GB) FROM 1TB
(D: 146 GB BAD SECTORS G: 146 GB GOOD, H: 172GB GOOD) FROM 500 GB HDD 
=================================================================

---

### Post by efflandt on 2015-02-06
OS independent games that use Open GL like minecraft can actually run faster natively in Linux than in Windows (judging from a 1 GHz 2 core, 2 GB tablet PC with Radian HD 6250 graphics running 32-bit Win7 Pro from 32 GB SSD vs. 64-bit Ubuntu or Lubuntu 12.04 from SD card). But that tablet PC does not have the speed or storage necessary for Steam.

I read that some Linux Steam games ported from Windows to Linux my have an extra layer that may slow them down somewhat. And I am not sure if wine has direct rendering either, since Linux Google Chrome (using HTML5 I think) appears to play Netflix videos in better resolution that Netflix Desktop using wine and MS Silverlight. But I have not run games in wine and rarely boot Windows at home, so I do not have any direct comparisons other than Unigine Valley running in 64-bit Win7 vs. 64-bit Ubuntu where Win7 running DirectX 11 is a bit faster. I have not played L4D2 for a while, but since you can play that in Windows or Linux, why don't you compare Windows vs. wine vs. Linux and tell us how they compare?

---

### Post by mooreted on 2015-02-06
Dota2 and Left4Dead2 run great on my desktop: Ubuntu 14.04 x64, 8GB RAM, Nividia Geforce GTX 650.

Games that I have run on Wine, mostly World of Warcraft, were kind of glitchy. I have decided for my own sanity that if it doesn't run natively on Linux, I don't need it.

On the other hand, Witcher 2 was not a very good port as they used their own layer similar to Wine and it doesn't run very well at all. All of the Steam games actually made for or properly ported to Linux run very well. Right now I'm addicted to Borderlands 2.

I currently have 28 Linux games on Steam.

---

### Post by oldrocker99 on 2015-02-08
> 

On the other hand, Witcher 2 was not a very good port as they used their own layer similar to Wine and it doesn't run very well at all. All of the Steam games actually made for or properly ported to Linux run very well. Right now I'm addicted to Borderlands 2.

I currently have 28 Linux games on Steam.

Virtual Programming, the folks behind the much-maligned eON wrapper used for The Witcher 2, have worked pretty diligently to improve that wrapper, and the second version of it was a huge improvement. There's now a beta version of eON which [http://www.gamingonlinux.com/articles/the-witcher-2-has-a-new-beta-for-linux-the-improvements-are-staggering.4892](http://www.gamingonlinux.com/articles/the-witcher-2-has-a-new-beta-for-linux-the-improvements-are-staggering.4892) says is a vast improvement over the second version. You might wish to give it another try. The second version of the wrapper worked very well for me; I have played several hours on that version without crashes, and looking great, and running fast enough to be quite enjoyable.

My desktop PC died (again:mad:), and, when it becomes fixed, I'll certainly try the beta wrapper.

---

### Post by mastablasta on 2015-02-09
> **mandarpowale said:**
> 
(I am dual booting UBUNTU 12.04 LTS with Windows XP SP3 32 bit)
, E: UBUNTU 25GB '/', 16 GB 'SWAP', 226GB '/home' F:463 GB) FROM 1TB


are you maybe using wubi or what? how can Ubutnu be on E: ? E: is Windows designation and if you have propper dualboot then Windows won't recognise the space Linux occupies.

> 1 TB WD PURPLE


Why are you using purple as system disk? they are ment for video survailance systems. i am sure they are not working as good as blue or black in system disk department. or am i wrong?

otherwise games with Linux version in steam will run on Linux without wine.

---

### Post by greg69 on 2015-02-17
It's very hit and miss. Personally I can get "Acceptable" framerates on PayDay 2 mid settings with wine. Wheras if I dual booted windows (Which I intend to do for those games) I should be getting 130 on high with my graphics card and CPU.
HDD won't affect framerates, Only load times.
Personally I run XUbuntu for gaming and I can play a ton of great games. Counter strike, 7 days to die, Borderlands 2, Dead island to name just a few.
WINE WILL DAMAGE FRAMERATES! It's unavoidable. It's a compatibility layer. Like trying to cram a round peg into a square hole, It won't be a perfect fit. There will sometimes be bugs, and always a performance hit. However significant.
Best option at the moment is dual booting. That way, You still get all the perks of Ubuntu (Namely the added speed on native games that have been well ported) And the compatibility of Windows. 

Note: Get a better Graphics card. I had the 7750 but then I upgraded to the GTX 760. I've never looked back. Budget cards aren't worth the elements they're made from.

---

### Post by mandarpowale on 2015-02-20
Is Xubuntu well on the UBUNTU website?

---

### Post by vasa1 on 2015-02-20
> **mandarpowale said:**
> Is Xubuntu well on the UBUNTU website?
What has that got to do with your original question?

---

### Post by mandarpowale on 2015-02-21
> **mooreted said:**
> Dota2 and Left4Dead2 run great on my desktop: Ubuntu 14.04 x64, 8GB RAM, Nividia Geforce GTX 650.

Games that I have run on Wine, mostly World of Warcraft, were kind of glitchy. I have decided for my own sanity that if it doesn't run natively on Linux, I don't need it.

On the other hand, Witcher 2 was not a very good port as they used their own layer similar to Wine and it doesn't run very well at all. All of the Steam games actually made for or properly ported to Linux run very well. Right now I'm addicted to Borderlands 2.

I currently have 28 Linux games on Steam.

Hi,

Did you have to use proprietory drivers from nVidia for gaming or are default Linux Drivers enough ? (Do I have to ensure that POSIX shared memory be enabled on the system?

I don't want to play anything other than L4D2 or Dota. (I'm not going to use Wine from now on)

Mandar

> **mastablasta said:**
> are you maybe using wubi or what? how can Ubutnu be on E: ? E: is Windows designation and if you have propper dualboot then Windows won't recognise the space Linux occupies.

Of course Windows Doesn't detect it, I meant that E: was 250GB partion from 1st drive (1 TB Purple), I hade an old HDD 500 GB which developed a bad sector of 768 kb on its OS Partition which now appears as D:.


> 
Why are you using purple as system disk? they are ment for video survailance systems. i am sure they are not working as good as blue or black in system disk department. or am i wrong? 

My assembler recommended it since my PC is on for longer hours (12-15 hrs daily).

---

### Post by mastablasta on 2015-02-24
> **mandarpowale said:**
> 
Did you have to use proprietory drivers from nVidia for gaming or are default Linux Drivers enough ? 

I don't want to play anything other than L4D2 or Dota. (I'm not going to use Wine from now on)

definitely use NVidia drivers for gaming.

> **mandarpowale said:**
> 
My assembler recommended it since my PC is on for longer hours (12-15 hrs daily).

perhaps they had a few lying around and couldn't sell them :-) black type would be best choice for games and OS. but often blue is good enough. definitely not green, purple or red (well red would be OK I guess but is more expencive). 

so I won't pretend I know that much about ru7nning OS on purple, but running OS on green could cause some issues with OS. for the same reason I would avoid purple for OS - it wasn't ment for that but for storage. it was made to support constant recording which is why it is mostly used on video surveillance systems.

---

