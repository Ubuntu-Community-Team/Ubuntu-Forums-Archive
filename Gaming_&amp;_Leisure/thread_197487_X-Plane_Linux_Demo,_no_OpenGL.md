---
title: "X-Plane Linux Demo, no OpenGL"
date: 2006-06-15
forum: Gaming &amp; Leisure
---

### Post by FlyingPenguin on 2006-06-15
Well I have my ATI 9700 mobility working with 3D and OpenGL just fine as far as I can tell. Games run as fast as they always have. However when I start Xplane is shows the splash/load screen for about 1 second and the log file created says:

"I can not find a 3-D accelerator card that can handle OpenGL that has correctly installed drivers. I will still let you run the simulator, but the frame rate will NOT allow for a good simulation. For you to fly realistically, you must use X-Plane version Classic, or get a 3-D accelerator card that can handle OpenGL."

Also, I can run the Plane Makeer and other program, only the actual X-Plane will not work.

---

### Post by lennyjames on 2006-08-31
I have the same problem. I am running an ATI9800 Pro with updated drivers. Has anyone got any idea how to get X-plane running? It sure would be nice to have in on Ubuntu...

---

### Post by RktMan on 2006-09-01
> **FlyingPenguin said:**
> Well I have my ATI 9700 mobility working with 3D and OpenGL just fine as far as I can tell. Games run as fast as they always have. However when I start Xplane is shows the splash/load screen for about 1 second and the log file created says:

"I can not find a 3-D accelerator card that can handle OpenGL that has correctly installed drivers. I will still let you run the simulator, but the frame rate will NOT allow for a good simulation. For you to fly realistically, you must use X-Plane version Classic, or get a 3-D accelerator card that can handle OpenGL."

Also, I can run the Plane Makeer and other program, only the actual X-Plane will not work.

i _had_ x-plane 8.40 running on Gento with an ATI 9800 Pro.

i has some issues that had to do with some "memory corruption" as diagnosed by some of the x-plane linux people.

i could get it to run, by setting an environment variable, ```
_MALLOC_CHECK=2
``` (i think that is what it was).

again, the linux guy for laminar seemed to think that it was the ATI driver that was really at fault.

since then, i've upgraded my hardware to an NVidia card, and my OS to Kubuntu.

on Kubuntu, i have to use the following shell script :

```
LD_PRELOAD=/usr/lib/libalut.so.0 ./X-Plane-athlon-xp
```

this has something to do with x-plane being built against an older version of OpenAL i think.

with this setup, x-plane seems to run GREAT !

i'm getting faster frame rates with Linux on this machine than i am with Windows.

now ... if i could only get my joystick hat switch working correctly.

x-plane sees it as an "axis" instead of a button ... so i can't use it for the 3D view like i usually do.

Tony

---

