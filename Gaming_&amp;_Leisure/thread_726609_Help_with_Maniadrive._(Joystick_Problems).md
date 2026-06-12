---
title: "Help with Maniadrive. (Joystick Problems)"
date: 2008-03-16
forum: Gaming &amp; Leisure
---

### Post by DarkSim on 2008-03-16
I installed Maniadrive from GetDeb recently and for some reason it will not recognize that I have a joystick plugged in.  This is strange because the joystick works with all the emulators and Wine programs I use it on and it is recognized by the OS as a Jess Tech USB 4-Axis 12-Button Gamepad.


Error Output Snipped:
```
j@rabiddustbunny:~$ maniadrive
Raydium: Raydium 3D Game Engine
Raydium: version 0.705
Raydium: command line args: OK
Raydium: chdir to './': OK
Raydium: using '/home/j/.mania_drive' as home dir
Raydium: Requesting 1024x768:32 mode
Raydium: Xinerama detected with 1 screens:
Raydium: *** screen 0 : 1280x1024 at (0,0)
Raydium: using Xinerama screen 0
Raydium: Found 1280x1024 with 24 bpp color and 24 bits zbuffer (stencil is 1)
Raydium: using GeForce FX 5500/AGP/SSE/3DNOW!, from NVIDIA Corporation (version 2.1.1 NVIDIA 100.14.19)
Raydium: Signal Handlers: OK
Raydium: OpenGL extensions: OK
Raydium: Platform "4xfloat" vector size is: 16 byte(s) long
Raydium: OpenGL implementation maximum texture size: 4096x4096
Raydium: OpenGL hardware providing 4 texture unit(s)
Raydium: vertex arrays memory: OK
Raydium: path: OK
Raydium: keyboard: OK
Raydium: mouse: OK
Raydium: /dev/input/event0: cannot open (rw), no Force Feedback.
Raydium: joy: FAILED (cannot open /dev/js0 and /dev/input/js0)

```

Anyone have an idea?

---

### Post by DarkSim on 2008-03-16
I got it to work thanks to the 8th post in of this thread:

[http://ubuntuforums.org/showthread.php?t=514701](http://ubuntuforums.org/showthread.php?t=514701)

---

### Post by acoustibop on 2008-03-17
I always put a symlink to js0 in /dev first thing after installing Ubuntu, DarkSim.  Saves so much hassle! ;)

---

