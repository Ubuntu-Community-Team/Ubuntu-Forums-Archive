---
title: "ATI glxgears"
date: 2006-10-07
forum: Desktop Environments
---

### Post by lorddaddy84 on 2006-10-07
Hello all, 
I have a onboard ati radeon x200, amd athlon 64, 1 gig of ram, and I am running dapper drake. I followed the wiki here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
to install the drivers from ati.com and when I run glxgears it doesnt go over 200 fps, please help.
> justin@justin-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6065 (8.29.6)
Thanks.

---

### Post by bladez90 on 2006-10-09
I have the same problem:

> 
evan@evan-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6065 (8.29.6)


> evan@evan-desktop:~$ glxgears
627 frames in 5.0 seconds = 125.398 FPS
567 frames in 5.0 seconds = 112.964 FPS
297 frames in 5.0 seconds = 59.289 FPS
296 frames in 5.0 seconds = 59.101 FPS
313 frames in 5.0 seconds = 62.447 FPS
313 frames in 5.0 seconds = 62.446 FPS
312 frames in 5.0 seconds = 62.396 FPS
312 frames in 5.0 seconds = 62.396 FPS
313 frames in 5.0 seconds = 62.446 FPS
312 frames in 5.0 seconds = 62.397 FPS

---

### Post by varean on 2006-10-09
Glxgears is not a benchmark to test performance.  You should test your drivers on a game to see if they are performing to your liking.  Generally, a glxgears output greater than 100 shows that you have 3d acceleration working, but not to what extent.

---

### Post by lorddaddy84 on 2006-10-10
> **varean said:**
> Glxgears is not a benchmark to test performance.  You should test your drivers on a game to see if they are performing to your liking.  Generally, a glxgears output greater than 100 shows that you have 3d acceleration working, but not to what extent.
So If the game works, and glxgears doesnt. Then it isnt really a problem?
Whats a good openGL game to test it with?
Thanks.

---

