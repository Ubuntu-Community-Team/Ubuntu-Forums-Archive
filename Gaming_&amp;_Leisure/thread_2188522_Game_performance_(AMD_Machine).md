---
title: "Game performance (AMD Machine)"
date: 2013-11-17
forum: Gaming &amp; Leisure
---

### Post by rpmcavoy on 2013-11-17
Hello everyone!

So I recently installed elementary os on a spare hard drive in my rig and though I'd test out gaming performance with steam and tf2. My system has 8gb ram (2x 4gb), a fx-6300 cpu, and two 7850 in crossfire with 2gb vram each. on windows I play tf2 great, no lagg hiccups or anything on the highest settings. when i go to try that on elementary OS I cant even play it on the lowest settings without having the game lagg pause and stutter. I also have the latest amd official beta drivers installed (which were a pain to do). 

Anyone have any suggestions? aside from the gaming performance I'm loving this OS. 

Thanks

---

### Post by Arthur_D on 2013-11-17
Either try enabling Crossfire, or if it's enabled already try actually disabling it. Sometimes drivers mess up with more than one card even though they theoretically should make things faster.

---

### Post by DanglingPointer on 2013-11-17
I would say crossfire and sli aren't mature yet on Linux.  I would conjecture that they will only mature by the second half of next year at the earliest due to market demand from SteamMachines (when it takes over the world :-D).

If you want to ditch M$ then unfortunately your best bet would be single GPU until Mantle-enabled games for Linux comes out utilising **asymmetric AFR** (asymmetric crossfire rendering, _**no**_ need to have similar gpus, you can get a smaller-weaker gpu to help a vastly more powerful gpu all sharing the same pool of memory) which does not need a driver for Mantle developed games if the game developer coded for the possibility of multi-GCN-gpus.  It puts the game engine developer on the driver's seat instead of AMD's Catalyst FGLRX.  The game will talk directly to the gpus (a.k.a direct to metal development like the consoles).

The 7850 is a GCN chip.

However I would say for legacy games AMD will improve crossfire which requires the Catalyst driver for symmetric AFR.

If you are wondering what the performance is of AMD GCN on Linux with modern game engines, check the benchmark results on posts 22 and 26 of the following thread...
[http://ubuntuforums.org/showthread.php?t=2183281&page=3](http://ubuntuforums.org/showthread.php?t=2183281&page=3)

---

### Post by rpmcavoy on 2013-11-17
Yep I had crossfire on when i wrote this post and I just tried it with out crossfire and got the same result on the lowest settings.

---

### Post by rpmcavoy on 2013-11-17
> **DanglingPointer said:**
> I would say crossfire and sli aren't mature yet on Linux.  I would conjecture that they will only mature by the second half of next year at the earliest due to market demand from SteamMachines (when it takes over the world :-D).

If you want to ditch M$ then unfortunately your best bet would be single GPU until Mantle-enabled games for Linux comes out utilising **asymmetric AFR** (asymmetric crossfire rendering, _**no**_ need to have similar gpus, you can get a smaller-weaker gpu to help a vastly more powerful gpu all sharing the same pool of memory) which does not need a driver for Mantle developed games if the game developer coded for the possibility of multi-GCN-gpus.  It puts the game engine developer on the driver's seat instead of AMD's Catalyst FGLRX.  The game will talk directly to the gpus (a.k.a direct to metal development like the consoles).

The 7850 is a GCN chip.

However I would say for legacy games AMD will improve crossfire which requires the Catalyst driver for symmetric AFR.

If you are wondering what the performance is of AMD GCN on Linux with modern game engines, check the benchmark results on posts 22 and 26 of the following thread...
[http://ubuntuforums.org/showthread.php?t=2183281&page=3](http://ubuntuforums.org/showthread.php?t=2183281&page=3)

I honestly cant wait till mantle starts being used, even for windows it will make things better, way better than having to use directx. and I would like to swap my dual gpu config for a single card equivalent but since I tried turning crossfire off I dont think dual gpu's are my problem right now.

---

### Post by dannyboy79 on 2013-11-18
something is definitely wrong, i could play TF2 on a 1.8Ghz C2D with an Nvidia 8400GS on low settings with no lag and was pulling around 15 FPS (still playable as far as that hardware goes anyway) maybe disabling crossfire isn't enough, did you disable the 2nd GPU in the BIOS and or have you tried the latest stable drive, not the beta driver?

---

