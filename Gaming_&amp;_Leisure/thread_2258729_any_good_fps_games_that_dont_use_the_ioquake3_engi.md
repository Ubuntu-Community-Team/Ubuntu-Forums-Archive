---
title: "any good fps games that dont use the ioquake3 engine?"
date: 2014-12-30
forum: Gaming &amp; Leisure
---

### Post by robert-mathew-harris on 2014-12-30
I'm curious if anyone knows of any good first person shooters that don't us ioquake3 as its engine. I know its an odd request by I'm having issues getting ioquake3 to run on this PPC powermac g5 with ubuntu 12.04. I've got a post up just recently in the Mac hardware section of the forums about my attempts. I havnt had any replies yet

---

### Post by mateo14 on 2015-01-07
I know that Sin was ported to Linux PPC, but I do not know any store that sell this game for Linux. Additionally. I know that game was ported many years ago, and I have never seen anyone who ran it on Linux PPC.

---

### Post by zombifier25 on 2015-01-07
If you're looking for something Quake-like, check out Sauerbraten. It's in the repo, simply install the package "sauerbraten".

There are also some big commercial FPSes on Steam and the like. Team Fortress 2, Borderlands, Left 4 Dead are the ones I can think up atm.

---

### Post by robert-mathew-harris on 2015-01-09
i might have to look into team fotress ive heard of it before. i did finaly get openarena to work. had to use a version from a newer ubuntu, but now i have to figure out video card + PPC issues.

---

### Post by oldrocker99 on 2015-01-11
There's also Metro:Last Light, Borderlands 2, the Half-Life 1 & 2 series, Painkiller: Hell and Damnation, Nuclear Dawn, and quite a few other FPS games on Steam for Linux.

What is your video card? Post the results of this:
```
lspci | grep VGA
```

For some informed help

---

### Post by robert-mathew-harris on 2015-01-11
I'm pretty sure i need to get a different card, ive got a whole other thread about it. non the les my results are...

lspci | grep VGA
0001:08:00.0 VGA compatible controller: NVIDIA Corporation NV43 [GeForce 6600] (rev a2)

but keep in mind its a PowerMac G5with ubuntu 12.04 ppc. thats where all my issues are mainly ppc and that card has isues with nouveau anyways from what ive read. so far ive had to compile the old open source NV driver from source to get a usable system. nouveau kept giving me gpu lockups or somthing

---

### Post by Benjamin_Eunice on 2015-01-11
well, there is a great database of linux games here: [http://www.lgdb.org/](http://www.lgdb.org/).

---

### Post by oldrocker99 on 2015-01-12
> **robert-mathew-harris said:**
> I'm pretty sure i need to get a different card, ive got a whole other thread about it. non the les my results are...

lspci | grep VGA
0001:08:00.0 VGA compatible controller: NVIDIA Corporation NV43 [GeForce 6600] (rev a2)

but keep in mind its a PowerMac G5with ubuntu 12.04 ppc. thats where all my issues are mainly ppc and that card has isues with nouveau anyways from what ive read. so far ive had to compile the old open source NV driver from source to get a usable system. nouveau kept giving me gpu lockups or somthing

OK, the 6600 should be able to use the proprietary nVidia driver, not open source. Do this:
```
sudo apt-get purge nvidia*
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-340
sudo shutdown -r now
```

The shutdown -r will reboot your computer, which is necessary to activate the new drivers. This will install the latest stable nVidia proprietary drivers, which **should** work with your 6600. 

Good luck, and post your results. IF there is an issue with the PPC, post that too.

---

### Post by robert-mathew-harris on 2015-01-13
well it could find it.

$ sudo apt-get install nvidia-graphics-drivers-340
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-graphics-drivers-340

Nvidia has never compiled their proprietary drivers for PPC that I know of.

---

### Post by oldrocker99 on 2015-01-13
My bad; I didn't realize that PPC isn't supported. This thread, although it's old, may be able to help:[http://ubuntuforums.org/showthread.php?t=1143179](http://ubuntuforums.org/showthread.php?t=1143179).

There's also this:[https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards](https://wiki.ubuntu.com/PowerPCFAQ#Nvidia_cards).

I regret that I couldn't help you further.

---

### Post by robert-mathew-harris on 2015-01-15
It's all good. I didnt until i started using this machine, PPC support is getting slack everywhere now it seems. ubuntu forums has been the best place for info by far.

---

### Post by mateo14 on 2015-01-15
> **robert-mathew-harris said:**
> It's all good. I didnt until i started using this machine, PPC support is getting slack everywhere now it seems. ubuntu forums has been the best place for info by far.


Unfortunately, I don't have a computer with the PPC processor, and I know that now producers do not care about games for Linux PPC. However, this machine can be still used for some games. I noticed that there is a short article about games for Linux PPC 


Candy Cruncher
Civilization: Call to Power
Dominions: Priests, Prophets & Pretenders  - box version
Dominions II: The Ascension Wars - box version
Dominions 3 - box version
Eric's Ultimate Solitaire
Gorky 17
Heroes of Might and Magic III 
Majesty Gold - Only first box version of Majesty Gold (without DRM)
Myth II: Soulblighter 
NingPo MahJong 
Railroad Tycoon II Gold Edition
Robin Hood: Legenda Sherwood
Sid Meier's Alpha Centauri with Alien Crossfire expansion pack
Sin 
Soul Ride 


[http://en.wikipedia.org/wiki/Linux_gaming](http://en.wikipedia.org/wiki/Linux_gaming)


All these games are now not officially supported by the producers, and you will need to rely on your knowledge to run these games successfully on Linux PPC. Some of them you will find on ebay, Amazon.com etc. or game stores for Linux.


Canceled Games


Ballistics 
Disciples 2: Dark Prophecy
Northland


I know that Duke 3D, Hexen, Heretic, Quake 2, Star Trek Voyager: Elite Force etc. were ported to Linux.

---

### Post by robert-mathew-harris on 2015-01-16
Yea there's a a few games still available, like I said earlier I got open arena installed no problem its just not playable right now. Nothing will be until I can figure out something video card wise. Right now open arena get about 1fps give or take a few lol. But I expect that right now because I'm stuck on the old open source NV driver, nouveau crashes quickly, I'm thinking because of temps, at idle the geforce 6600 is hitting 81c at idle with nouveau driver, osx is around 51c, I think there's a little difference.

---

