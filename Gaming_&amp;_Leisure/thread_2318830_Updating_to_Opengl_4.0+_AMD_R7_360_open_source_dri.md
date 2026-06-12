---
title: "Updating to Opengl 4.0+ AMD R7 360 open source drivers"
date: 2016-03-29
forum: Gaming &amp; Leisure
---

### Post by Retlol on 2016-03-29
I want to play Metro: Last Light redux but the game kindly let me know I don't have Opengl 4.0 support. I'm using the open source drivers. I tried to use the closed sourced ones (from Additional Drivers) but this caused my Ubuntu Mate 15.10 to be stuck on the loading screen so I had to revert back. 

```
rw@linuxbox:~$ glxinfo | grep OpenGL
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD BONAIRE (DRM 2.43.0, LLVM 3.6.2)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 11.0.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 11.0.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 11.0.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:

```

---

### Post by Retlol on 2016-03-30
Managed to get the closed source drivers working after updating my system (which support Opengl 4.5).

---

### Post by mastablasta on 2016-03-31
after about 6 months it will only be opensource drivers called amdgpu. currently these are still under heavy development (I think you could load them with newer kernel, but if fglrx works then there is no need). with 16.04 they will be the driver of choice. but they will likely still be in beta. for old cards only the opensoruce radeon driverwill eb available.

---

### Post by Retlol on 2016-04-01
I presume my card (r7 360) will be supported as it's one of their current cards (build is only 3 months old). I do know it's based off an older card tho. I won't be updating to 16.04 until I know the card is supported by the new open source drivers. I do also use options in the catalyst manager and I hear that's also no implemented yet.

I build this PC myself with Windows 10 in mind but that turned out to be a disaster for multiple reasons. I was planning to update the card to an r9 390 later but I'll prob change to NVIDIA as they seem better supported on Linux. I'll wait for the new AMD drivers go live to make up my mind, I'm willing to give them a shot but I have my doubts.

The current closed source drivers work a lot better than the MESA (I think) drivers but the performance is still quite a bit behind the Windows versions in my experience of the games I've played thus far (Left for Dead 2, LoL (wine), Dota 2, Metro: Last Light redux).

---

### Post by Retlol on 2016-04-01
Nope the r7 360, it's a GNC 1.1 card and the driver is meant for GNC 1.2 cards. Even a R9 390X isn't supported (one of their newest flagship cards).

---

