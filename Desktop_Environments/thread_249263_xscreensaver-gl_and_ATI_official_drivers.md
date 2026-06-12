---
title: "xscreensaver-gl and ATI official drivers"
date: 2006-09-02
forum: Desktop Environments
---

### Post by meimato on 2006-09-02
I recently upgraded my video card to an ATI X1600, which is not supported by the fglrx drivers shipped with ubuntu dapper.
So I installed the 8.27.10 official ATI drivers, and everything seems to work: fglrxinfo dislays the following

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.5946 (8.27.10)

and here is fgl_glxgears report:

Using GLX_SGIX_pbuffer
2049 frames in 5.0 seconds = 409.800 FPS
2117 frames in 5.0 seconds = 423.400 FPS
3541 frames in 5.0 seconds = 708.200 FPS
2751 frames in 5.0 seconds = 550.200 FPS
3515 frames in 5.0 seconds = 703.000 FPS
2352 frames in 5.0 seconds = 470.400 FPS
2400 frames in 5.0 seconds = 480.000 FPS


I've got a problem with xscreensaver-gl: it is VERY slow, it runs as in my system there were no 3D card functioning.
The same thing happen on my laptop, which has a mobility RADEON 9600.

---

### Post by varean on 2006-09-02
I know this is a bit off topic, but what installation guide did you use to get your X1600 working?  I beleive I have the same card and I haven't gotten the drivers to work yet.

---

### Post by meimato on 2006-09-02
This one. Good luck.

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

### Post by meimato on 2006-09-03
Noone having this strange issue with opengl screensavers?

---

### Post by meimato on 2006-09-05
Still waiting for someone who can help me...

---

