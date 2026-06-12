---
title: "Tribal Trouble - No Sound"
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by gdeyoung on 2006-07-14
I've seen some posts on OpenAL problems, but it didn't seem to apply here.

I have a new install of 6.06 LTS.  I install Tribal Trouble and it works great, but no sound.  I have sound in other applications.  I even have sound in Chromium which is another OpenAL game.

Here is the output from my std.err file, it looks like it finds OpenAL.  Anyone else having this problem?  Any Ideas?

std.err output:


Xrandr extension version 1.1
Using Xrandr for display mode switching
XF86VidMode extension version 2.2
Initial mode: 1440 x 900 x 16 @60Hz
Removed 0 duplicate displaymodes
getPathFromClassLoader: searching for: openal
getPathFromClassLoader: Path found: /home/gdeyoung/tribaltrouble/gamedata/data-1/native/.svn/text-base/libopenal.so.svn-base
getPathFromClassLoader: searching for: lwjgl
getPathFromClassLoader: Path found: /home/gdeyoung/tribaltrouble/gamedata/data-1/native/.svn/text-base/liblwjgl.so.svn-base
Found 7 OpenAL paths
Testing '/home/gdeyoung/tribaltrouble/gamedata/data-1/native/.svn/text-base/libopenal.so.svn-base'
Found OpenAL at '/home/gdeyoung/tribaltrouble/gamedata/data-1/native/.svn/text-base/libopenal.so.svn-base'
Removed 0 duplicate displaymodes
Mode 0: 1680x1050 @60
Mode 1: 1440x900 @60
Pixel format info: r = 5, g = 6, b = 5, a = 0, depth = 24, stencil = 0, sample buffers = 0, samples = 0
Using NetWM for fullscreen window
Created window
Pixel format info: r = 5, g = 6, b = 5, a = 0, depth = 16, stencil = 0, sample buffers = 0, samples = 0
Mode 0: 1680x1050 @60
Mode 1: 1440x900 @60
XF86VidMode extension version 2.2
Mode 0: 1680x1050 @60
Mode 1: 1440x900 @60
XF86VidMode extension version 2.2

---

### Post by Fredo on 2006-08-09
Hi!

I had the same problem. It helped to create a file .openalrc in $HOME containing the following lines:

-----8<-----
# Contains user settings for OpenAL
# Goes in ~/.openalrc

# Use ALSA (valid: sdl, native, alsa)
(define devices '(native))
----->8-----

Using "alsa" didn't work for me, no idea why.

Hope, it works for you, too.

Fredo

---

### Post by gdeyoung on 2006-09-28
That works great!  Thanks!

---

### Post by bludimnd on 2009-04-25
> **gdeyoung said:**
> That works great!  Thanks!

Doesn't work for me. What exact settings did you use?

---

