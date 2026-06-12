---
title: "Cant run 3d desk"
date: 2006-10-17
forum: Desktop Environments
---

### Post by geniusvicks on 2006-10-17
I tried to install XGL and Beryl (using methods given in [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL))  but it didnt work. Now I cant run 3d desktop which I could do before I installed XGL etc.

The error is given below:

geniusvicks@Home:~$ /usr/bin/3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.1
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

Plz help!!!

---

### Post by ayoli on 2006-10-17
i dunno about 3ddesk, you may have something wrong in your xorg.conf. does dri works ?
what's the output of 
```
glxinfo |grep dri
```
btw, if you want beryl, since it seems you have an i915 graphics chipset, you should use AIGLX instead of XGL, look [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX")

---

### Post by geniusvicks on 2006-10-18
[B]This is the output:
[/B]
i915 DRI driver expected DDX version 1-1.5.x but got version 1.4.1
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering

No I'm quite sure I have Intel 845 xx

---

### Post by ayoli on 2006-10-18
does your xorg.conf modules section load dri, and have this section uncommented:
```
Section "DRI"
        Mode    0666
EndSection
```

---

### Post by geniusvicks on 2006-10-18
It is aldready uncommented.

---

