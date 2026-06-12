---
title: "gfceu widescreen nightmare!"
date: 2007-11-25
forum: Gaming &amp; Leisure
---

### Post by El Lance-O on 2007-11-25
I have searched for days for any shred of help on this subject and have found nothing.

When I run gfceu, it works fine but when it goes fullscreen it doesn't want to stretch.

I have tried -xres/-yres, -stretchx/y, -x/yscale, and everything else in between.

Is gfceu just unable to run under a 16:9 resolution? I've even tried switching my resolution to 1024x768 with no luck.

Oh, and my default is 1280x800 by the way.

And yes, I do have all of these in my xorg.conf file, so there shouldn't be a reason why it won't work unless it is gfceu.

Should I just switch to another emulator? And if so, which one has a decent GUI and is somewhat similar to gfceu?

Thanks ahead of time, I really appreciate any responses.

---

### Post by jondecker76 on 2007-11-25
Do you actually want to stretch a 4:3 ratio output to a 16:9 ration display? Your games will be "stretched" horizontally and it actually effects playability.

I can run fceu in either widescreen or 4:3 on my widescreen monitors - but I found that running true widescreen distorts the picture too much for my taste. 

Running a 4:3 ratio on my widescreen fills the screen vertically, and centers it horizontally so there are just 2 vertical black bars on either side of the picture.  I would think that this is what anyone would want...

here are the settings I use:
(my monitor resolution is 1680 x 1050)

fullscreen 16:9
-xres 1680 -yres 1050 

fullscreen 3:4
-xres 1400 -yres 1050



Note that 1400x1050 isn't a standard resolution - its the resolution of the output window you want..  Also, I might have had to use the -stretchx/y but can't remember right now


hope this helps

---

### Post by jondecker76 on 2007-11-25
one more thing - 

I no longer use fceu - i find that mednafen is a much better emulator (and supports many more systems). the command line options are similar also.... Here is a launch string for a game where I do a fullscreen 4:3 ratio on my 16:9 flatscreen (using mednafen)-

```

mednafen -sound 1 -sounddriver alsa -sounddevice "sexyal-literal-default"  -fs 1 -nes.xres 1400 -nes.yres 1050 -nes.stretch 1 "/home/jondecker76/ROMS/Nintendo/Super Mario Bros. 3 (E).nes"

```

---

### Post by El Lance-O on 2007-11-25
Oh I have no problem with horizontal distortion, I have ZSNES and ePSXe do that with no problem.

It doesn't bother me as much as having black bars. I like having my screen used to it's full advantage.

I've tried just putting 1280x800 in the xres/yres argument, but it doesn't register it whatsoever. In the terminal it says it's setting it to that resolution, but it clearly doesn't.

Blehhhhh...

---

### Post by jondecker76 on 2007-11-25
give mednafen a try...  on my setup I get about double the FPS i did with fceu..  There is no good user interface or front end (yet - i'm actually working on one now for mednafen)

---

