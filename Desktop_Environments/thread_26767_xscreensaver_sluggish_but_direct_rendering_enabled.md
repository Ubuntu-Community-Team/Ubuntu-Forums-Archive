---
title: "xscreensaver sluggish but direct rendering enabled"
date: 2005-04-13
forum: Desktop Environments
---

### Post by Ashera on 2005-04-13
All the 3D screensavers in xscreensaver are really sluggish for me. They seem to run fast in the small-screen preview (the one you get when you click on the screensaver in the list), but when viewed as a full-screen preview, it takes a very long time to calculate each frame.

I'm a Linux newbie; I'm running Warty on a Dell Inspiron 8100. I managed to get the nVidia GeForce2 Go set up. When I run glxinfo, it says "Direct rendering: Yes". The resolution is set correctly (1400x1050).

I can play Tux Racer fine, and I can run glgears as a stand-alone program (it gets 600-700 fps). However, if I try to run it as a screensaver, it's really, really slow.

What should I do?

---

### Post by graabein on 2005-04-14
I'm having serious problems with glx... glxinfo just gives me segmentation fault (and nothing else). 
Anyone know where to start debugging?

---

### Post by gil-galad on 2005-04-14
It sounds like the screen savers are simply too much for your video card to handle.  Xscreensaver has some pretty fancy opengl rendering, and it probably is just running slow, especially at 1400x1050.

---

### Post by zafar on 2005-04-17
[QUOTE=gil-galad]It sounds like the screen savers are simply too much for your video card to handle.  Xscreensaver has some pretty fancy opengl rendering, and it probably is just running slow, especially at 1400x1050.[/QUOTE]
 I don't think it is a problem with the video card. I have a relatively old system (600mhz p3) with a Geforce 2 MX, but when i use to run fedora core 3 before i converted to ubuntu... i could run the glmatrix screen saver with 20-25 fps no problem, but now when i run it in hoary with DRI and the latest nvidia drivers, i get around 1 fps. There is defintely a problem, but i can't seem to figure out what it is.

---

### Post by jazzer on 2005-04-18
Sounds like perhaps your 'xscreensaver-gl-helper' is not linked to the right OpenGL library (check this with 'ldd /usr/bin/xscreensaver-gl-helper').  The one provided by nvidia.  Check and see if /usr/lib/libGL.so.1 is linked to /usr/lib/libGL.so.1.0.nvidia_version (you can check this with 'ls -l /usr/lib/libGL.so.1')  It sounds like xscreensaver is not getting 3d acceleration.  

On another note, my desktop as a whole in Ubuntu seems faster than FC3; but glxgears reports about 100-200fps less than in FC3 - not too worried about it though, I'd trade system response for that.

---

### Post by zafar on 2005-04-18
I checked the links and they all seem to be correct. I'm also experiencing a faster desktop in Ubuntu than FC3 and less glxgears fps (about 50 which i don't mind..).

After using the xscreensaver program for a bit and alot setting changing, I'm pretty sure that the small preview window in the program is using hardware accelleration. After the 'preview' button is clicked or the screensaver runs due to inactivity, the screensaver runs slow and not hardware accellearted.

---

### Post by zafar on 2005-04-21
I've Noticed something else.. i've got an openGL visualization for music and it runs very fast windowed for all sizes until you resize it to more than 1008x736 (my desktop resolution is at 1280x1024). As soon as its resized over that, the performance drops down to about 1 fps. This is also what i am noticing with the screen savers.

---

### Post by jazzer on 2005-04-22
How did you install the nvidia drivers?  Did you use the ones provided in the warty repositories or did you download directly from nvidia?  Myself, I used synpatic and grabbed the ones that were in the repositories.  I'm not having any problems with glx other than that it is a little bit slower than in FC3....

---

### Post by zafar on 2005-04-22
Actually, I'm using hoary since i couldn't find any threads that were as related as this one. I'm using the latest nvidia drivers from the ubuntu repositories.

Edit: I've started a thread in the Ubuntu 5.04 Hardware help section here: [http://www.ubuntuforums.org/showthread.php?t=29061](http://www.ubuntuforums.org/showthread.php?t=29061)

---

