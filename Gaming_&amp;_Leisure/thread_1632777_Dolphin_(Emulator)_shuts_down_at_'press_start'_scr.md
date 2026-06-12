---
title: "Dolphin (Emulator) shuts down at 'press start' screen."
date: 2010-11-28
forum: Gaming &amp; Leisure
---

### Post by rich52x on 2010-11-28
Okay, I've got Dolphin installed, and my ISOs (which I own copies of) ready. But, I'll load it up and start the game, but as soon as I press enter at the 'PRESS START' screen, it spontaneously shuts down, the render window and the emu window, no error messages or anything. The game in question is Luigi's Mansion, which I really would like to play, so, any help?

---

### Post by thatguruguy on 2010-11-28
How recent is your copy of dolphin-emu?  I suggest getting the ppa: [https://launchpad.net/~glennric/+archive/dolphin-emu]("https://launchpad.net/%7Eglennric/+archive/dolphin-emu")

You might also pose questions on the dolphin-emu forums: [http://forums.dolphin-emu.com/index.php](http://forums.dolphin-emu.com/index.php)

Do any other roms work, or do you always get the same results?

---

### Post by rich52x on 2010-11-29
My dolphin emulator is SVN R 6186, but i think they released a newer one not long ago. Thanks for the PPA, and I've also tried running Zelda: Twilight Princess to no avail, it just closes after around 5 seconds of emulation.

---

### Post by thatguruguy on 2010-11-29
Are you talking about zelda twilight princess for the wii?  Because I have that one and it works fine.  Have you tried running dolphin-emu from a terminal, to see what kind of error messages you get?

---

### Post by rich52x on 2010-11-29
I mean the GC version, I've not tried any Wii games. I opened it from a terminal and this is the output 
```
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:77: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:77: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:78: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:93: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:172: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:202: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:310: Murrine configuration option "style" is no longer supported and will be ignored.
/home/richard/.themes/Dust Mac/gtk-2.0/gtkrc:344: Murrine configuration option "style" is no longer supported and will be ignored.
07:23:545 Source/Core/Common/Src/FileUtil.cpp:97 W[COMMON]: IsDirectory: stat failed on /home/richard/.dolphin-emu/Wii/title/00000001/00000002/content: 
07:24:121 Source/Core/DolphinWX/Src/X11Utils.cpp:115 N[Video]: XRRExtension-Version 1.3
07:24:306 Source/Core/DolphinWX/Src/X11Utils.cpp:158 N[Video]: Fullscreen Resolution 640x480

```

A lot of that is pretty irrelevant I assume, but make what you will of it :D

---

### Post by sephiroth42496 on 2011-04-15
hello im having the same kinda of problem but with the gc version of the game it crashes right after the Nintendo logo and im running on the r7443 release 32 bit version any help would be really useful ive been dying to play this for a while :confused:

---

