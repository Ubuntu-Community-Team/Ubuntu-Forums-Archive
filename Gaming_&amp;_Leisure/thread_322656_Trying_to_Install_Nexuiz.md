---
title: "Trying to Install Nexuiz"
date: 2006-12-20
forum: Gaming &amp; Leisure
---

### Post by Count on 2006-12-20
I have downloaded the newest Nexuiz version, this is my first time installing it. I have unziped the .zip file, and when I navigate to 
 
 Count@ninja:~/Nexuiz$ 
 
 and enter 
 
 ./nexuiz-linux-glx.sh 
 
 I get 
 
 Console initialized. 
 Nexuiz Linux 17:03:05 Dec 12 2006 
 Trying to load library... "libz.so.1" - loaded. 
 Compressed files support enabled 
 Added packfile data/common-spog.pk3 (26 files) 
 Added packfile data/data20061212.pk3 (2884 files) 
 Trying to load library... "libcurl.so.3" - loaded. 
 cURL support enabled 
 Initializing client 
 Trying to load library... "libvorbis.so.0" - loaded. 
 Trying to load library... "libvorbisfile.so.3" - loaded. 
 Ogg Vorbis support enabled 
 couldn't exec config.cfg 
 couldn't exec data/campaign.cfg 
 couldn't exec autoexec.cfg 
 Starting video system 
 Video: fullscreen 800x600x32x60hz 
 Loading OpenGL driver libGL.so.1 
 Xlib: extension "GLX" missing on display ":0.0". 
 Couldn't get an RGB, Double-buffered, Depth visual 
 Desired video mode fail, trying fallbacks... 
 Video: fullscreen 800x600x32x60hz 
 Loading OpenGL driver libGL.so.1 
 Xlib: extension "GLX" missing on display ":0.0". 
 Couldn't get an RGB, Double-buffered, Depth visual 
 Video: fullscreen 800x600x16x60hz 
 Loading OpenGL driver libGL.so.1 
 Xlib: extension "GLX" missing on display ":0.0". 
 Couldn't get an RGB, Double-buffered, Depth visual 
 Video: fullscreen 640x480x16x60hz 
 Loading OpenGL driver libGL.so.1 
 Xlib: extension "GLX" missing on display ":0.0". 
 Couldn't get an RGB, Double-buffered, Depth visual 
 Video: window 640x480x16x60hz 
 Loading OpenGL driver libGL.so.1 
 Xlib: extension "GLX" missing on display ":0.0". 
 Couldn't get an RGB, Double-buffered, Depth visual 
 Quake Error: Video modes failed 
 
 With ./nexuiz-linux-sdl.sh I get an error message also, but it is much longer so I am going to leave it out unless requested. Hopefully this is enough information, and thanks in advance for the help.

---

### Post by K.Mandla on 2006-12-20
Forgive me for asking, but is there a reason you're not using the one in the repositories?

[http://packages.ubuntu.com/edgy/games/nexuiz](http://packages.ubuntu.com/edgy/games/nexuiz)

---

### Post by Count on 2006-12-21
When I downloaded it, I had failed to realize that there was a package. I am a complete newb with Ubuntu and Linux in general, and now that I have downloaded it "manually" I would like to see if I can get it to run, because I have a fairly slow internet connection, and I would rather not have to wait on downloading again, if I could get it to run as it is. If I can't or someone else can't figure out the problem, I will install it with apt-get.

---

### Post by Perfect Storm on 2006-12-21
Have you enable/installed 3D acc. driver for your card?

---

### Post by pay on 2006-12-21
Run ```
glxinfo | direct rendering
```and see if the video card is set up.

---

### Post by Count on 2006-12-21
Here is the error from glxinfo | direct rendering

bash: direct: command not found
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


I used the envy script to configure my card, it is a Nvidia Riva TNT2, and also, here is the device information from /etc/X11/xorg.conf 

Section "Device"
        Identifier      "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
        Driver          "nvidia"
        BusID           "PCI:1:5:0"
        Option          "UseFBDev"              "true"
EndSection

---

### Post by pay on 2006-12-22
Try using this guide to get it working [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by K.Mandla on 2006-12-22
How long ago did you use the envy script? It looks like Alberto [updated it]("http://albertomilone.com/wordpress/") as little as 10 days ago, and the update affected the legacy driver -- which [your TNT2 should use]("http://www.nvidia.com/object/IO_32667.html").

You might just want to install the legacy driver from the repositories, to see if you can get it working that way.

```
sudo aptitude install nvidia-glx-legacy
```

Edit: Are you sure your card can even handle Nexuiz? or the GLX extension? If I remember right, Vantas were mid-grade video cards for office desktop machines. I've seen them in Pentium II Gateways here at work.

[http://www.nvidia.com/page/vanta.html](http://www.nvidia.com/page/vanta.html)

---

### Post by Count on 2006-12-22
> **K.Mandla said:**
> How long ago did you use the envy script? It looks like Alberto [updated it]("http://albertomilone.com/wordpress/") as little as 10 days ago, and the update affected the legacy driver -- which [your TNT2 should use]("http://www.nvidia.com/object/IO_32667.html").

You might just want to install the legacy driver from the repositories, to see if you can get it working that way.

```
sudo aptitude install nvidia-glx-legacy
```

Edit: Are you sure your card can even handle Nexuiz? or the GLX extension? If I remember right, Vantas were mid-grade video cards for office desktop machines. I've seen them in Pentium II Gateways here at work.

[http://www.nvidia.com/page/vanta.html](http://www.nvidia.com/page/vanta.html)


I updated using envy last night, and it had no effect. Also, installing nvidia-glx-legacy will cause X to crash on reboot. As for it's capabilities, I was hoping that I would be able to disable some of the effects and also go into low-res.

---

