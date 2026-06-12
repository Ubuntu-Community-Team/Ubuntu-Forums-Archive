---
title: "Dota 2 bad!! Fps"
date: 2013-08-22
forum: Gaming &amp; Leisure
---

### Post by snafu006 on 2013-08-22
So ya i been playing dota 2 now and the performance sucks. I think it driver based but befor i get in to it all here the spec of computer.

Hp Laptop G62
AMD CPU
ATI HD 4250
8 G ram

First Test ubuntu 12.04.1 with 13.1 Proprietary drivers.

Lots of crashing and poor FPS 10-15

Secound Test 13.4 with Open source 
```
snafu@snafu-HP-G62-Notebook-PC:~$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL version string: 3.0 Mesa 9.3.0-devel (git-86751cb raring-oibaf-ppa)
OpenGL shading language version string: 1.30
OpenGL extensions:

```

But The FPS crap 0.1 to 3 unplayable

Is there anyone out there that got this game playing better ?

Also way i am trying the open source is that i read the open source drivers are stable and are able to play steam game's and it will but shi$y FPS.

And FU ati from droping support and steam FU for not helping with ati drivers when half your supported game's support old ati harware

This is from steam Dota 2 Minimum spec


[LIST]**Minimum:** 

[LIST]
[*]**OS:** Ubuntu 12.04 
[*]**Processor:** Dual core from Intel or AMD at 2.8 GHz 
[*]**Memory:** 4 GB RAM 
[*]**Graphics:** nVidia GeForce 8600/9600GT, ATI/AMD Radeaon HD2600/3600 (Graphic Drivers: nVidia 310, AMD 12.11), OpenGL 2.1 
[*]**Network:** Broadband Internet connection 
[*]**Hard Drive:** 8 GB available space 
[*]**Sound Card:** OpenAL Compatible Sound Card
[/LIST]
[/LIST]

Ok i feel better.

---

### Post by oldrocker99 on 2013-08-22
The nvidia-current package, I beleieve, is 3.13; I tried 3.25 and it borked my system until I purged nvidia* and installed nvidia-current. I run DOTA 2 on my desktop (Athlon Phenom II 965, nVidia 650Ti) and it runs at full speed.

---

### Post by oscarivera9 on 2013-08-23
Hi,
I just started playing Dota 2 last night as a matter of fact and I thoroughly enjoyed it.  I had no problems at all.  I think your problems might be related to the hardware that you're using.
My specs are:

[LIST]
[*]AMD FX 6100 3.3GHz CPU 
[*]8 GB RAM 
[*]ATI/Radeon HD 5770 GPU 
[*]AMD 13.1 Graphics Driver 
[*]Ubuntu 12.04.1 64-bit 
[*]Cooler Master Hyper 212 EVO CPU cooler 
[*]WD 1TB HDD 
[/LIST]
I played through the first couple of tutorials (I'm new to the game) and I didn't have any problems whatsoever.  Even though you appear to be meeting the posted minimum requirements, I know for a fact that laptop processors tend to get hotter than desktop processors due to the difference in cooling options available.  For my AMD FX 6 core CPU I use a Cooler Master Hyper 212 EVO CPU cooler to maintain my core temperature as low as possible.  I've often found hot temperatures to be the cause for the sort of problems you're describing.

---

### Post by DarkAmbient on 2013-08-23
Did you install the proprietary drivers using "additional drivers" menu, or manually from AMD?

---

### Post by mJayk on 2013-08-23
Is it an AMD APU / Graphics card combo - drivers for them cause bad performance in linux atm

---

### Post by oscarivera9 on 2013-08-24
> **DarkAmbient said:**
> Did you install the proprietary drivers using "additional drivers" menu, or manually from AMD?

I've used "additional drivers" in the past, but not this time.  Due to Steam being available on Ubuntu, AMD is actually working closely with both Ubuntu and Steam to make it easy for us gamers to install the drivers we need.  When you start Steam, if you don't have the suggested drivers, a dialog box will appear telling you what you need to get.  Open up the Ubuntu Software Center and simply type in what Steam suggests and the Ubuntu Software Center will install it for you.  Of course, if you've already installed other drivers in the past, you may need to remove these, preferably through the Terminal.

---

### Post by mJayk on 2013-08-24
I have to say im so impressed atm with the native steam games DOTA 2 just got a really nice update on steam which enables it to use the system messages feature. I also get faster loads and smoother play in ubuntu than I do in win 7.

Really impressed, enabled me to remove win 7 completley

---

### Post by mastablasta on 2013-08-26
the OP computer meets the requrements (unless they are wrong). so it should work just fine. however i can only wonder if Unity is interfering in this case? might be good to try another desktop. 

i agree about AMD doing mistake with dropping support for those cards. especially since steam says games support them/need them... and no one wanted new features in those old drivers only support.

---

### Post by erazor84 on 2013-11-30
i am running ubuntu 13.10 with the latest 13.10 beta drivers from amd. and i have 2-20 fps in dota 2. also killing floor runs like and old grandma. very low performance :( only half life 2, CS Source, and other Valve games runs "good" but not perfect. serious sam 3 stutter like hell on ultimate settings. on medium it run ok with lag sometimes ...

on windows i can run this games maxed out without any problem.

my specs:

amd phenom II 965
amd radeon HD 5870
8GB Ram

There is much work to do for amd ... their drivers are bad as always :( maybe i will buy a nvidia graphics card, because i cannot game very well with amd.


sorry for my english ;) in the past i tried alternative distris like mint with cinnamon. the performance was a little better, but the overall performance was bad, like on ubuntu itself. so it must be amd's fault. not cannonicals with unity.

---

### Post by dannyboy79 on 2013-11-30
i would suggest using 2d unity or a different desktop manager like openbox for only when you're going to game, you can choose which desktop to boot to in the greeter. anything besides unity as it's more graphic intensive. also, are you using the propritary AMD drivers? it's fglrx, i am using the latest stable catalyst which is 13.04 i believe. i have an HD5750 and an HD7770 and can play serious sam 3 at almost 60FPS.

---

