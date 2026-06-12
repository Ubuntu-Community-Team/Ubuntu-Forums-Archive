---
title: "Quake4 Oddness."
date: 2006-06-02
forum: Gaming &amp; Leisure
---

### Post by rivethead on 2006-06-02
Ive installed quake4 and have copied all the correct files over on Dapper 6.06 LTS, i also have installed the new Nvidia 8762 driver for my Nvidia 6800 GO Ultra ( Dell XPS Gen2 ). My problem is when i go to run quake4 it starts to load then spits out this message. 

> ---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1920 x 1200
1024 x 768
800 x 600
640 x 480
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1920 x 1200
1024 x 768
800 x 600
640 x 480
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
--------------- BSE Shutdown ----------------
---------------------------------------------


Glxgears runs fine, and in my glxinfo i checked that the " direct rendering: Yes " was there and set to " Yes " as i saw that with some other people that was there problem. 

Ive tried a few things with the xorg.conf but im not sure im linux savy enough to figure this problem out on my own. If anyone could offer any advice or fixes it would be appriciated.

-Rvt

---

### Post by rivethead on 2006-06-02
!!POSSIBLE FIX!!


For those who may be having the same problem i just now seemed to correct mine. Here is what i did.

First i checked my xorg.conf again just to make sure everything was correct and i noticed the color depth was set to 16 bit so i changed that to 24 bit. I remember distinctly trying to run the game with this already set at 24 and it not working correctly. However i took a peek though synaptic package manager again and found  
"libsage0 - Support OpenGL in SDL applications " i installed this and all the sudden i was able to load and play quake. Still there was one thing left, quake 4 loaded with all video fine but the sound was horribly boofed up. After a little research on quake 4 +set commands i found some people who run it in linux using this to launch the game " quake4 +set s_driver oss " after doing that with the previous fixes above implemented, everything runs amazingly smoothe,  and pulls about 10 frames better than my windows install. I run a constant 63 frames in multiplayer mode now at resolution 1280x768 (16:9). I hope this can help someone else. But i wanted to reply to my post just to let the community know that i corrected the problem.

-Rvt

---

### Post by walovaton on 2006-09-18
Where did you get Quake 4 for Linux??

---

### Post by MetalMusicAddict on 2006-09-18
> **walovaton said:**
> Where did you get Quake 4 for Linux??

You use the normal retail disk. There installers for linux from id and on the web.

---

### Post by Drevan on 2006-09-19
I'm actually just updating my drivers right now. I still have yet to try them out on the laptop to see if I can get some extra fps out of the games I run on cedega. Hopefully this driver update will net me some extra fps in quake 4 though. I already notice it is much smoother than windows though.

---

