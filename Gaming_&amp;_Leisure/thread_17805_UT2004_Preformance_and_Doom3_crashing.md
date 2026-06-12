---
title: "UT2004 Preformance and Doom3 crashing"
date: 2005-03-02
forum: Gaming &amp; Leisure
---

### Post by darkoptix on 2005-03-02
Hey, I decided to install Unreal Tournament 2004 to see how the preformance was on linux. I have a 9800 pro card, and on windows I could put all the settings on high without any problems. Now on linux, I can put the settings on all high/med/lowest, and I still get this little glitch ups ever odd 3 or 5 seconds. I thought this could be ati's drivers or something, however quake 3 runs flawlessly(why wouldn't it.. :)) and doom 3 gets excellent framerates on high settings, untill crashing 5 minutes in(I really have no idea why).

I checked all my settings, and my card is setup fine. here is the output from fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)

I've tried other kernels, settings, lots of things, and I cannot seem to get it to run without these little glitch ups every couple of seconds, and Doom3 crashing after about 5 minutes of gameplay. Is it just teh gay ati drivers, or have I not set something up on this system right?

System Specs:
athlon xp 2800+
asus a7n8x mobo
1 gig of ram
ati 9800 pro

---

### Post by jimarko on 2005-03-10
My specs are in my sig, and here's my output from fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)

I have the same problem, i get a killer framerate for about 5 - 10 minutes, and then it just drops out. I also run UT2004, ET, and Q3, all of which run fine with no dropouts. If i can get some form of log out of D3 i'll dump the important parts of it here.

If anyone has a suggestion or two, that'd be highly appreciated.


EDIT: Hrm.. sig not workin at the moment, but here it is:

 The rig:
MSI K7N2G MB
Athlon XP 1800+
512 DDR400 SDRAM
ATI 9800 PRO 128MB
SB LIVE! emk10k1
120 GB Western Digital

All held together with a Lian Li 6087a

---

### Post by dermotti on 2005-03-11
I had similar issues with my 9700....i threw in the towel :-(

---

### Post by jimarko on 2005-03-11
Yeah, that seems to be the general consensus regarding ATI & linux.. Still, I'll keep on digging and I'll post anything of interest here for others to try :)

---

### Post by jimarko on 2005-03-11
Ok, here is the final piped output of Doom3 from when it crashed:

signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
--------- Game Map Shutdown ----------
--------------------------------------
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------


What I have discovered is that the crash does not occur in any one point of the starting map, but rather at a certain time, say after around 5 minutes of gameplay. This only happens in singleplayer, as i can run around, shoot stuff and move from area to area with no slowdowns or crashes in a LAN multiplayer server.

I have also found that right before it crashes, the level goes dark and the lights 'tear', as if they were solid textured entities in the game. Very strange.

Your thoughts?

---

### Post by darkoptix on 2005-03-12
I have that identical error jimarko... Also I have the same time for gameplay before the drop. 
However, UT2004 works perfectly for you? I get these little hiccups of lag every little bit on any setting... Is there some setting to change.

---

### Post by jimarko on 2005-03-12
I have stuttering all through UT2004, but its probably the worst in Onslaught-based matches. I have found that switching off precaching for textures helps a little bit in maps like DM-deck17, but overall there is no merit. 

I think dermotti is right, unless we all wish to wait for ATI to bring out some decent drivers, its probably best to start advertising our ATI cards for sale if we're are serious about gaming on Linux   ](*,)  :-x 

*looks at nv 6800 evily*

---

### Post by darkoptix on 2005-03-13
I know my old computer (P3 600mhz 256 ram gefore4 mx440), which I wouldn't be able to run much, Doesn't have the studders in Ut2004, Doom3 doesn't crash(Doesn't run well, but that isn't comparable), and call of duty works fine... All these games got crashs, or graphical screwups on my much better computer with an ati card. Proof that those ATI drivers suck.
Yeah, i'm thinking of selling my 9800 and maybe buying a 6800 if I can make the extra cash somewhere... The only problem is finding someone to buy the card. :(

---

### Post by jimarko on 2005-03-13
Hrm.. I am running a NForce 2 chipset, so I might use the on-board GF4 MX 440 and try it for test/diagnostics sake. 

I'll post my findings and info as soon as I do that.

EDIT: would it be possible to have the NVIDIA drivers and ATI drivers installed at the same time so I can test both card's 3D performance just by switching the monitor cable?

Hrm.. I'll have a play

---

### Post by jimarko on 2005-03-14
Well, after a re-install of drivers and the removal of my 9800 PRO, I found my on-board graphics (GF4MX440) worked BETTER than my 9800 pro. How sad.

Oh yeah, when I say better, I am referring to games such as UT2004 (no stuttering) and Tribes 2 (no z-buffer tearing or general crappiness)

Unfortunately my ATI has been delegated to paperweight duties for the moment, but I'll hopefully find a buyer that uses a win32-based system. 

Now I understand that this doesn't help someone without access to a secondary 3D card, but my findings conclude that the ATI drivers are not very er... good. There, thats a nice way of putting it.

Hope it helps


Thanks


jimmy

---

### Post by Super_staunch on 2005-03-14
I have a Amd Athlon64 3200+ and MSI K8neo2 platinum mobo 256mb ddr400 ram and a geforce 5200 ultra and am running wary64 and doom3 doesn't even start up, surley my comp can run doom3! but why does it not start up!!!! :-k

---

### Post by Pse on 2005-03-14
This is a problem I am having as well. My guess is that Doom3 is looking for its libraries in the wrong folder, probably trying to use 64-bit libs instead of 32-bit...
I've heard some people have been succesful in running Doom3 in a 32-bit chroot on a 64-bit Ubuntu.

---

### Post by Super_staunch on 2005-03-14
forgive my" newbieness" but how does one do that? [-o<

---

