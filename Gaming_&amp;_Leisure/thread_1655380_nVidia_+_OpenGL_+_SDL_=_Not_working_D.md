---
title: "nVidia + OpenGL + SDL = Not working D:"
date: 2010-12-29
forum: Gaming &amp; Leisure
---

### Post by danopia on 2010-12-29
This is one of the few times I'm starting a topic here, because normally the problems I come across are a simple fix, are well-documented, or are small enough to not matter. However I have a very large problem on my main desktop system involving any 3D game which uses SDL to manage a window: it just doesn't work.

A common message would be "Unable to set video mode: X11 driver not configured with OpenGL", but the first phrase differs from program to program.

This problem has been stalking me since Hardy was the latest release, and here I am at Maverick without a resolution. (I have reinstalled once or twice along the way, but the current install is an upgraded 10.04). The final result is always frustration, and I end up either using my laptop (which can't handle as much graphical awesome as my desktop) or not using SDL and/or the game that requires it.

Please do not tell me to Google the error message. I have. I'd estimate about 10 combined hours of researching this problem. I have reinstalled SDL and every single package that uses it (because of how apt works, it was the only way to do a complete remove/clean/install cycle on SDL, but I also tried `apt-get reinstall`). I have installed SDL from source, and `configure` says that '--enable-video-opengl' defaults to 'yes'. I'm pretty sure that I ran that reconfigure command line for Xorg on multiple occasions. I've done basically everything that has been suggested in other topics.

I'm running 10.10 on an Intel desktop system, 2.2 GHz dual-core Pentium. The graphics card is an nVidia 8600 GTS. I'm using nvidia's proprietary drivers.

Just to be clear, the issue is ONLY with SDL and OpenGL. UrTHD in WINE works, Compiz works, Minecraft (Java) works, glxgears works (at 2500 fps). When a 3d app runs, it tends to run very well.

The problem seems to be common among nVidia users, btw.

---

### Post by efikkan on 2010-12-29
Enter glxinfo in terminal and post the output.

Try reinstalling the proprietary drivers or try a different version.

---

### Post by danopia on 2010-12-29
glxinfo output: [https://gist.github.com/188cdd334a806a78ae33](https://gist.github.com/188cdd334a806a78ae33)

I am not really sure what driver I am using. I can tell you this:
```
danopia@danopia:~/Dev/SDL-1.2.14$ dpkg -l|grep nvidia
ii  nvidia-173-modaliases     173.14.28-0ubuntu1 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-185-kernel-source  260.19.06-0ubuntu1 Transitional package for nvidia-glx-185-kernel-source
ii  nvidia-185-libvdpau       260.19.06-0ubuntu1 Transitional package for nvidia-185-libvdpau
ii  nvidia-185-modaliases     260.19.06-0ubuntu1 Transitional package for nvidia-185-modaliases
ii  nvidia-96-modaliases      96.43.19-0ubuntu1  Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-cg-toolkit         3.0.0007-0ubuntu1  Cg Toolkit - GPU Shader Authoring Language
ii  nvidia-common             0.2.24             Find obsolete NVIDIA drivers
ii  nvidia-current            260.19.06-0ubuntu1 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-modaliases 260.19.06-0ubuntu1 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-glx-185            260.19.06-0ubuntu1 Transitional package for nvidia-glx-185
ii  nvidia-settings           260.19.06-0ubuntu1 Tool of configuring the NVIDIA graphics driver

```

The driver was installed automatically by the proprietary driver utility. I'll take suggestions on which packages etc. I should be using for an nVidia GeForce 8600 GTS.

---

### Post by efikkan on 2010-12-29
Try running glxgears in terminal and check if it displays any error messages.

Do you have any non-SDL games? I think the enemy territory quake wars demo does not use SDL.

You are using the 260.19.06 driver (default in Ubuntu 10.10). Try removing it's packages completely (in synaptic) and reinstall the driver. If this does not help, try the 173-driver. If there is still no luck, go to nvidia.com and download the latest driver. Let me know if you want some help with this.

---

### Post by danopia on 2010-12-29
As I said in the OP: "Just to be clear, the issue is ONLY with SDL and OpenGL. UrTHD in WINE works, Compiz works, Minecraft (Java) works, glxgears works (at 2500 fps). When a 3d app runs, it tends to run very well." I'll add to that: normal UrT (4.1), a native Linux game, also works.

I'm going to try the different drivers versions now, and I'll probably report back within an hour or so.

Thanks for your time!

---

### Post by xclusive585 on 2012-11-18
Well, years after the OP, I am in the same damn boat. I've scoured the net and found no working solution.  Using LinuxMint13 (Ubuntu12.04), And an Nvidia GT 630 with proprietary drivers (295.4) installed.  Just like the OP, My issue is specifically with opengl, glx.  Any programs that require glx or SDL just crash. (Blender, sdl-ball, nibbles; just for examples, there are countless others as I said ANYTHING using glx/sdl) 

Just like the op the error messages I get are along the lines of "Xlib:  extension "GLX" missing on display ":0.0". /build/buildd/blender-2.62/intern/ghost/intern/GHOST_WindowX11.cpp:193: X11 glXQueryVersion() failed, verify working openGL system!"

In checking out my system it seems I simply have no OpenGL support, No GLX support etc.

glxinfo produces a similarly related error:
> me@mine ~ $ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Linking lib.so*** to here or there didnt work. 
Yes, of course I've tried reinstalling drivers, several times, many versions, same outcome.
Yes, Ive reconfigured x-org etc, several times, makes no difference
Configuring alternatives for glx doesn't work as there are "no alternatives available"


I've been pulling my hair out like the OP. My onboard video is worthless, and if I cant use my nvidia card, this is worthless to me.

---

### Post by thatguruguy on 2012-11-18
> **xclusive585 said:**
> Well, years after the OP, I am in the same damn boat. I've scoured the net and found no working solution.  Using LinuxMint13 (Ubuntu12.04), And an Nvidia GT 630 with proprietary drivers (295.4) installed.  Just like the OP, My issue is specifically with opengl, glx.  Any programs that require glx or SDL just crash. (Blender, sdl-ball, nibbles; just for examples, there are countless others as I said ANYTHING using glx/sdl) 

Just like the op the error messages I get are along the lines of "Xlib:  extension "GLX" missing on display ":0.0". /build/buildd/blender-2.62/intern/ghost/intern/GHOST_WindowX11.cpp:193: X11 glXQueryVersion() failed, verify working openGL system!"

In checking out my system it seems I simply have no OpenGL support, No GLX support etc.

glxinfo produces a similarly related error:

Linking lib.so*** to here or there didnt work. 
Yes, of course I've tried reinstalling drivers, several times, many versions, same outcome.
Yes, Ive reconfigured x-org etc, several times, makes no difference
Configuring alternatives for glx doesn't work as there are "no alternatives available"


I've been pulling my hair out like the OP. My onboard video is worthless, and if I cant use my nvidia card, this is worthless to me.

You may have better luck posting your question on the Mint forums, rather than necromancing this old thread.

---

### Post by xclusive585 on 2012-11-18
I will be trying at mint forums but due to the nature of the issue and the fact that this relates directly to kernel modules, I definitely think this falls into Ubuntu's territory.

Mint is just the front-end, so to speak. And this thread exists, unsolved, identical issue.

---

