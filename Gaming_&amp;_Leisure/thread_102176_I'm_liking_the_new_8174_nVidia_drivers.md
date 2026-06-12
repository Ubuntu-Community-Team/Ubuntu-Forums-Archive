---
title: "I'm liking the new 8174 nVidia drivers"
date: 2005-12-11
forum: Gaming &amp; Leisure
---

### Post by kidcharles on 2005-12-11
I had a stuttering problem in opengl rendering in all games (particularly World of Warcraft) with the 7000 series, but this new set (8174) has totally eliminated it. I highly recommend trying them.

---

### Post by 23meg on 2005-12-11
They introduce new bugs as well, such as the screen size bug in 6200 chips (and I think some 6600 ones too) which makes the drivers completely unusable on cards equipped with them. The bug is confirmed, and no patches were promised so far, since the bug may be in the closed source part of the drivers.

---

### Post by Perfect Storm on 2005-12-11
Well, I havn't seen any diffrences in the new driver, but it could be that I'm using a older graphic card.

---

### Post by alynx on 2005-12-12
what does this mean ? 

Does the new driver help on the lagg i have  in World of warcraft???

I have a gforce 6600 GT 128 MB with the 7667 driver (think it was 7667)

I would have been the happiest badger if i could get World of Warcraft to run smooth

---

### Post by kidcharles on 2005-12-12
alynx, I have the same card (6600 GT), and had massive slow downs in certain areas (Mystic Ward in Ironforge, The Drag in Ogrimmar, and Arathi Basin) and just a generally stuttery experience, where there were constant short pauses. That's gone now with these drivers. I think I may have actually lost some fps, but I'd rather have that than the jerkiness of those pauses. I found that the stuttering was worse with the 7667 driver (I believe the one in the official package) than with the 7174 driver so I had been using that one up until now.

---

### Post by livingtarget on 2005-12-12
Just for the record as I have a 6600 chip (256 meg) too and I installed it today after I switched kernel and it works fine for me.

Didn't notice any real changes, ut2004 still plays as smooth as ever.

---

### Post by alynx on 2005-12-12
[QUOTE=kidcharles]alynx, I have the same card (6600 GT), and had massive slow downs in certain areas (Mystic Ward in Ironforge, The Drag in Ogrimmar, and Arathi Basin) and just a generally stuttery experience, where there were constant short pauses. That's gone now with these drivers. I think I may have actually lost some fps, but I'd rather have that than the jerkiness of those pauses. I found that the stuttering was worse with the 7667 driver (I believe the one in the official package) than with the 7174 driver so I had been using that one up until now.[/QUOTE]

im sorry to bother you with this noob question , but how do I change into that driver ? the 7174 .... 

I did the sudo apt-get install nvidia-glx and that is the 7667 drivers i belive

---

### Post by kidcharles on 2005-12-12
> im sorry to bother you with this noob question , but how do I change into that driver ? the 7174 .... 

I would suggest following "Method 2" at this post:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

If you run into any problems, come back here and ask.

One thing to note: If you decide you don't want the new drivers and want to go back to the officially packaged ones, you run "sudo sh NVIDIA-Linux-x86-1.0-8174-pkg1.run --uninstall". After that re-install the nvidia-glx and nvidia-settings packages (I think these are the only two needed?).

---

### Post by madjinx on 2005-12-12
Im loving the whole SLI on linux thing. My next rig which is almost complete is gonna be SLI, itll be fun to play with.

---

### Post by AndersAA on 2005-12-12
it might introduce some new bugs, but if fixes some that has been damn annoying for me.

Like hardlock switching between tty's on amd64.

---

### Post by hellfire_bg on 2005-12-13
> what does this mean ?

Does the new driver help on the lagg i have in World of warcraft???

I have a gforce 6600 GT 128 MB with the 7667 driver (think it was 7667)

I would have been the happiest badger if i could get World of Warcraft to run smooth
Hmm... Interesting my configuration is CPU - Athlon Xp 2200+, GPU - FX5200, 512mb ram and i had no problems playing World of warcraft (using cedega) and i was using the 7667 drivers. I installed it on windows and copied the instalation to my ubuntu partition. I just had to follow the instructions from here - [http://cedegawiki.sweetleafstudios.com/wiki/World_of_Warcraft](http://cedegawiki.sweetleafstudios.com/wiki/World_of_Warcraft) to avoid some bugs and got it working as smooth as it was on windows. I have also read that it works very well with wine too.

---

### Post by alynx on 2005-12-13
Well i Use Wine , since I really dont want to pay anything :) hehe

I got wine configured right and the game is running nice and without bugs as i mentioned.  But it is choppy/laggy , and the FPS is like 10-20

In windows my normal FPS is around 60 +

So i have no idea of what makes it lag then , maybe wine itself ? 

I use the wine 0.9.1 though

---

### Post by ubuntu_demon on 2005-12-13
From [https://wiki.ubuntu.com/NvidiaTVOut](https://wiki.ubuntu.com/NvidiaTVOut) :
S-VIDEO does not work with the 1.0-7667 drivers, do not use the hyphen

Does anyone know whether this is solved with 8174 ?

---

### Post by AndersAA on 2005-12-13
[QUOTE=ubuntu_demon]From [https://wiki.ubuntu.com/NvidiaTVOut](https://wiki.ubuntu.com/NvidiaTVOut) :
S-VIDEO does not work with the 1.0-7667 drivers, do not use the hyphen

Does anyone know whether this is solved with 8174 ?[/QUOTE]

I never had any problems with svideo out on any nvidia driver and I've used em for ages.

---

### Post by Snipersnest on 2005-12-14
Can anybody tell me why my Ubuntu would still load and yet the screen never shows?  The sounds play in the background but video never shows up...heres my link I've never had this problem before.
 
If you have an idea PLZ link me or tell me.. I want to use my SLI in linux badly!

[http://www.ubuntuforums.org/showthread.php?t=102826]("http://www.ubuntuforums.org/showthread.php?t=102826")

---

### Post by ubu-for on 2005-12-15
[QUOTE=alynx]Well i Use Wine , since I really dont want to pay anything :) hehe

I got wine configured right and the game is running nice and without bugs as i mentioned.  But it is choppy/laggy , and the FPS is like 10-20

In windows my normal FPS is around 60 +

So i have no idea of what makes it lag then , maybe wine itself ? 

I use the wine 0.9.1 though[/QUOTE]

Just try Wine 0.9.3! [http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by Snipersnest on 2005-12-15
[quote=Snipersnest]Can anybody tell me why my Ubuntu would still load and yet the screen never shows? The sounds play in the background but video never shows up...heres my link I've never had this problem before.
 
If you have an idea PLZ link me or tell me.. I want to use my SLI in linux badly!
 
[http://www.ubuntuforums.org/showthread.php?t=102826]("http://www.ubuntuforums.org/showthread.php?t=102826")[/quote]
 
Well I found my problem...CRT is the default monitor over a DVI connection..I was using screen clone in Windows on a VGA cable to my 56in TV.. 
 
Only other question I have.. How do you test your SLI connection?

---

