---
title: "Problem with aiglx/compiz on radeon mobile 7500"
date: 2006-08-26
forum: Desktop Environments
---

### Post by elvislu on 2006-08-26
I've installed aiglx and compiz according to [http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)

The Xorg-air starts sucessfully but when I enter compiz-start in the terminal, my window borders disappeared, the gnome-panels shrank. Sometimes the system even halted. Anyone knows what's wrong?

Some logs that I think have something to do with the problem
1. The warnings in the /var/log/Xorg.0.log
> (WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xf1fff000 is: 0xf1fff000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xec7fec00
(WW) Warning, couldn't open module theatre_detect
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32


2. glxinfo|grep direct
> libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes


3. The console output when I run compiz-start
> gnome-window-decorator: no process killed
libGL warning: 3D driver claims to not support visual 0x4b
compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
compiz.real: water: GL_ARB_fragment_program is missing
Can't use gconf-dump plugin with gconf plugincompiz.real: pixmap 0x34000d6 can't be bound to texture
compiz.real: Couldn't bind redirected window 0x1000003 to texture
compiz.real: pixmap 0x34000d8 can't be bound to texture
compiz.real: Couldn't bind redirected window 0x100002a to texture
compiz.real: pixmap 0x34000da can't be bound to texture
compiz.real: Couldn't bind redirected window 0x2e00066 to texture
compiz.real: pixmap 0x34000dc can't be bound to texture
compiz.real: Couldn't bind redirected window 0x2c0001e to texture
compiz.real: pixmap 0x34000de can't be bound to texture
compiz.real: Couldn't bind redirected window 0x160001e to texture
--replace: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
--replace: No manageable screens found on display :0.0


---

### Post by PathSpace on 2006-08-26
Everyone who has installed AIGLX/Compiz has been having these problems after upgrading.  :(

---

