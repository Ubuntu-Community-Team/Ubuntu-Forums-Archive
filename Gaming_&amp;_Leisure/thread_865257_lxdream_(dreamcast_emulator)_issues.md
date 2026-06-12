---
title: "lxdream (dreamcast emulator) issues"
date: 2008-07-20
forum: Gaming &amp; Leisure
---

### Post by tjwoosta on 2008-07-20
i am running ubuntu hardy 64bit

i just installed lxdream dreamcast emulator (compiled from source)

all seemed to go well

but now when i try to run lxdream this is what happens
```

tj@tj-laptop:~/lxdream-0.8.3$ lxdream
01:40:40 00000000 WARN  Unable to load file 'bios/dcboot.rom': No such file or directory
01:40:40 00000000 WARN  Unable to load file 'bios/dcflash.rom': No such file or directory
01:40:40 A0000000 WARN  Not using direct rendering - this is likely to be slow
tj@tj-laptop:~/lxdream-0.8.3$ 

```

i understand the part about the bios but it wont even stay open long enough for me to use the GUI to set the bios directory

it just pops up with the GUI for lxdream in the background and another popup window on top that says 
> Unable to create render buffers (requires either EXT_framebuffer_object or GLX 1.3+)
followed by this popup when i close the other one
> Video driver 'gtk' failed to initialize (could not connect to display?)

then everything disapears 

any ideas?

**see the screenshot for a better understanding** (the green text you see is just my terminal window in the background showing through because i have window transparency from compiz enabled) 

btw, i know this should work fine because i have many other emulators running with great success (opengl and all)
(PCSX2, TuxCube, pSX, Mupen64Plus, Yabause, gens, snes9express, VBAexpress)

so what the hell is going on with lxdream?

---

### Post by FranMichaels on 2008-07-21
[http://www.lxdream.org/faq.php](http://www.lxdream.org/faq.php)

> What video hardware is supported?
Any currently supported Nvidia or ATI hardware should work fine using their supplied drivers. (as in, hardware that's still supported by its manufacturer) Provided suitable GL driver support was available (and this unfortunately is the ***big problem*** at the moment), any hardware capable of providing at least a 24-bit depth buffer should work to some degree. 

emphasis mine.

---

