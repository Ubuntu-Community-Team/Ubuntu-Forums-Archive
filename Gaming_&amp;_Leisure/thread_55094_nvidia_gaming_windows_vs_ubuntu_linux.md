---
title: "nvidia gaming windows vs ubuntu linux?"
date: 2005-08-07
forum: Gaming &amp; Leisure
---

### Post by holr on 2005-08-07
hello!

Im not starting a war here on which do you think is better, rather asking your kind advice in if it is worth getting an nvidia card.

I currently have an ati card (firegl 2 mobility - like a 9600) and i have found that games that run native under linux beat their windows counterparts (doom 3 runs much much smoother under ubuntu with 8.14.13 drivers than under windows with the latest). However, I have been playing with cedega lately, and have noticed that another of my faves, morrowind, runs much slower on ubuntu than on windows.

I completely understand that directx is basicly being emulated, so my question is, for those here with nvidia cards, do you notice much of a performance difference between games running on windows to games (i.e. directx)  running through cedega / wine?

Thanks!

---

### Post by drizek on 2005-08-07
it will always be slower in cedega, no matter what. but nvidia makes better linux drivers than ATI does, and the 6600gt is a great deal(should be about twice as fast as a vanilla 9600 in windows, even more under linux).

---

### Post by Lord Illidan on 2005-08-07
If you run linux games as native, like Doom 3, then performance will be better or equal to their windows counterparts.

However, if you are running windows games under Linux with an emulator like Cedega, then performance should be worse, as it is being emulated, unless you have no tasks running in the background...

---

### Post by artinla on 2005-08-07
I find that native linux games such as Doom3, Quake3, UT2004, America's army, etc all play with equal or better performance compared to their Win32 counterparts.

Cedega games are usually about 70% as fast as the windows version.  For example, I get around 400fps in Medal of Honor in Windows, around 300fps in cedega.

I am running three different NVidia systems, a 5950u, a 6600, and a 6800u.  All of them exhibit similar performance hits in cedega.  It is still nice to be able to run virtually all of my windows games in Ubuntu, so I think a little sacrifice in performance is still very acceptable.

Art

---

### Post by evilghost on 2005-08-07
FarCry, and some of the more D3D engine specific games will suffer more.  FarCry is jittery under Cedega even when running Low/Medium detail values at 1024x768.  Each game will differ depending on it's intensity.

UT2004 runs well under Linux however there are issues with the NVIDIA drivers only exposing 4 TMU's, so shadowing, vehicle license plates, in-game monitor textures, and powercores are affected.  ATI is not afflicted by this TMU issue because I believe they expose 8 TMUs versus 4.  UT2004 requires 6 to render all textures correctly.  However, ATI's does not have the same dedication of resources to the Linux community that NVIDIA does and their cards are not as robust under Linux as NVIDIAs.

---

