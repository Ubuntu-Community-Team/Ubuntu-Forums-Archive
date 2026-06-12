---
title: "Guild Wars and WoW Issues"
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by Seraed on 2007-07-14
Ok, so in [this thread]("http://ubuntuforums.org/showthread.php?t=498069") someone else had trouble getting Guild Wars up and running. I replied with the problem I was having which I thought was the same as his, though now in light of new information I'm sure it is not.

I am getting the 'unsupported hardware message' in regards to my video card. I was pretty sure at that point that it was just isolated to Guild Wars, though I just ran WoW and it too gave me an error message saying my video card is unsupported (when running in OGL, in Direct X it freezes during the loading screen after the character select).

They had both worked fine before. And I've updated Wine to 9.40 (whatever apt-get found in the wine repos). I used Envy to update my video card drivers too, still getting these problems. Any advice?

Also, since I'm here, anyone got City of Villains working with Wine 9.40? I've tried to run it but it has issues freezing after the Updater runs. The AppDB does not have any new info since before Feisty's release.

---

### Post by Nkari on 2007-07-16
I have the not supported under WoW as well when I set it to GL mode. I want to try and get that goigng to see if I can get all the way into the game, currently I also get stuck at the splash screen that comes up after I select a character.

Same version of Ubuntu and Wine, graphics drivers also updated with Envy

I using a couple of GeForce.7600 cards in this machine and I am running 64 bit since I have a Core2Duo processor and it seemed like the right choice.

I am wondering if it is possable that somehow wine is not setup with GL properly somehow despite the fact that the rest of the system is. Is that even possable? How could that be tested?

I really cant see why in GL mode Wow decides my video card is just not good enough.

others have mentioned that perhaps these errors appeared after the last WoW patch, but that was updated before I started trying to get the game running on this machine, its a new PC and I would really rather not run and Windows on it.

I am starting to wonder if running it under windows 2000 loaded into a VM might be easier than making it work through wine in my case, Game ran fine on my windows 2000 box (athlon 550, 512M and a 128M Radeon 9200). Even running Ubuntu and Windows 2000 in a VM may theoretically leave the game with more resources than I had on the other machine.

WoW has been the only thing really keeping me on Windows for last few months, and the seeming success people have had running it using Wine prompted me to not bother even putting any version of windows on this box and heading straight for the Ubuntu Disks. This could make it hard if I end up having to dualboot to play WoW.

---

### Post by Seraed on 2007-07-17
> **Nkari said:**
>  Same version of Ubuntu and Wine, graphics drivers also updated with Envy

I using a couple of GeForce.7600 cards in this machine and I am running 64 bit since I have a Core2Duo processor and it seemed like the right choice.

I am also running amd64, so maybe its just us 64 bit losers :lol:

> 
others have mentioned that perhaps these errors appeared after the last WoW patch, but that was updated before I started trying to get the game running on this machine, its a new PC and I would really rather not run and Windows on it.
I don't think it is WoW that is the problem, since I have stated above, that both GW and WoW suddenly stopped working for me. I'd say it is Wine, nVidia drivers, or just some update to our 64 bit Ubuntu installs.

I am also having problems with Doom 3... running natively, though I haven't had the chance to check in a few days to bother to see what the problem with Doom 3 was. If it was a graphics snaffu, then I can rule out Wine as the problem, and maybe even Ubuntu. And if that is the case I'll just have to remove the drivers that Envy installed and see if the basic nVidia drivers packed with Ubuntu work.

> 
I am starting to wonder if running it under windows 2000 loaded into a VM might be easier than making it work through wine in my case, Game ran fine on my windows 2000 box (athlon 550, 512M and a 128M Radeon 9200). Even running Ubuntu and Windows 2000 in a VM may theoretically leave the game with more resources than I had on the other machine.

I don't think that works since emulators also emulate hardware and lack the 3D acceleration, but feel free to tell me I'm wrong since I've next to no experience in that area.

> 
WoW has been the only thing really keeping me on Windows for last few months, and the seeming success people have had running it using Wine prompted me to not bother even putting any version of windows on this box and heading straight for the Ubuntu Disks. This could make it hard if I end up having to dualboot to play WoW.

True that... I have had tons of success with running WoW with Wine in the past and so my only tie to Windows (aside from Ventrilo, which I've got working with Wine now...) was gone. I have quit the game since, and shed myself of Windows on my main machine. I've got another box that I test stuff on with removable hard drives, so I use Windows for CoV now... still trying to get it to work with Wine since that machine is a POS.

Also, the Wine repository just added a 9.41 build. Gonna try to see if that changed anything before I start removing stuff ><

---

### Post by Seraed on 2007-07-19
So it seems it is a graphics issue.

Here is what happens when doom3 dies on me.  I run 'doom3', it goes into a blank screen, then dumps this on the terminal.
```
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()

```

Very ugh... Especially since Envy is awesome but is obviously not doing something right. Oh, I noticed that Envy is using nvidia-glx instead of nvidia-glx-new

I've got a 7800 GS (AGP) and so it should be using nvidia-glx-new. If I ditch Envy and install nvidia-glx-new then my system gets the funky do error of:

Fatal Server Error: No screens found.

The nv driver works, but I can't run things like beryl (or any other 3d acceleration). So I'm better off using the nvidia-glx driver to have something operable.

---

### Post by Nkari on 2007-07-19
Maybe we need a little input on what seems as far as you can tell to be a driver issue from Mr Envy himself. Posts on here as TSElliot, he may be able to clear things up a bit, seems to know a lot of random stuff about things relating to Video card drivers also.

On a side note I discovered the Virtual machine Idea was not going to work when I started playing with it, need the paid version of VMWARE to make it MAYBE work.

Messing around with setting up a dual boot backwards to how most people do it at the moment, Getting windows to like my hardware has so far been a little harder than it was in Ubuntu. I mean sure I can get a GUI working straight off and I have drivers on disk, but appart from getting video cards working straight off everything else like sound has been a nightmare, It can't even figure out that I have two onboard network cards with the Chipset drivers installed.

Once I fixed GRUB again windows died in a screaming blue heap (not different drives so I didn't overwrite the MBR on the Windows drive, so with some tricky drive re-mapping in GRUB I can it to load a bluescreen. I think Windows may have half installed an update all by itself when I was updating the WOW install on there and broke itself, getting GRUB working again was co-incidental.

---

### Post by Seraed on 2007-07-20
> **Nkari said:**
> Maybe we need a little input on what seems as far as you can tell to be a driver issue from Mr Envy himself. Posts on here as TSElliot, he may be able to clear things up a bit, seems to know a lot of random stuff about things relating to Video card drivers also.

That would be awesome :P

I was following the instructions he had put together on gaming.gows.org HowTo for Nvidia drivers. But with no luck as I stated above.

> 
I think Windows may have half installed an update all by itself when I was updating the WOW install on there and broke itself.

That has happened to me more than often enough... Though my solution to most Windows problems (such as that) is to format, reinstall, etc. I even set up my partitions for the eventuality that I will screw up Windows :P

Goodluck with BSOD!

---

