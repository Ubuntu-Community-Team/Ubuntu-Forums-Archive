---
title: "opengl error on quake4"
date: 2007-03-29
forum: Gaming &amp; Leisure
---

### Post by paf69 on 2007-03-29
I am very new to linux but i got quake4 installed and when the game tried to load up it gave me this error. How do I fix it?

--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x960 1280x800 1280x768 1152x768 1024x768 960x720 960x600 928x696 896x672 840x525 
800x600 720x450 700x525 640x512 640x480 640x400 640x384 576x384 512x384 400x300 
320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1280x1024 1280x960 1280x800 1280x768 1152x768 1024x768 960x720 960x600 928x696 896x672 840x525 
800x600 720x450 700x525 640x512 640x480 640x400 640x384 576x384 512x384 400x300 
320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Unable to initialize OpenGL

---

### Post by conjur3r on 2007-03-29
You will need to install your video card drivers.  What type of video card is it?

---

### Post by paf69 on 2007-03-29
Nvidia 7200 SE "Slow Edition"

---

### Post by paf69 on 2007-03-29
thx for the help....i used a program called auto matix and got the drivers i needed

---

