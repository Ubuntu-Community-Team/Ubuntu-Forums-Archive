---
title: "UT2K4 mouse problem"
date: 2008-08-12
forum: Gaming &amp; Leisure
---

### Post by dynamicres on 2008-08-12
i just installed unreal tournament 2k4 on hardy, did it from the anthology disk and was impressed as to well it worked on Linux until i actually got into a game.
The mouse, it acts as though im still in a window so it will not let the mouse move a full 360+ spinning around.
it will only go so far as the imaginary "window" settings will allow it to, aka say i'm running 1280x1024, it only allows me to move the mouse left 512 of those pixels and same with the right.

Does anyone know what could be causing this? my Linux build is very new, and im using fairly standard hardware, also, as for vid drivers im using the "advanced" built in nvidia drivers givin to me by the Linux install while using pretty graphics.

---

### Post by kdorf on 2008-08-12
This is a known issue with Unreal Tournament. I don't know myself what causes it as I haven't experienced it, but I think it may be that your X server is running at a different resolution than UT and this screws something up.

Try running UT at the same resolution as X and see if this fixes the problem. You can also try running UT in another X server, search the forums for a guide.

---

### Post by Brebs on 2008-08-12
What's the mouse driver - evdev or "mouse"? Look in /var/log/Xorg.0.log

I would try the other driver ;)

Also, try this [export command](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/189958):
```
export SDL_VIDEO_X11_DGAMOUSE=0
ut2004
```

DGA occasionally causes problems, for reasons that no-one has yet figured out.

---

