---
title: "UT2004 DM-Hyperblast-2 performance woes"
date: 2007-06-27
forum: Gaming &amp; Leisure
---

### Post by psyopper on 2007-06-27
OK - first off, my system:
Feisty/ 2.6.20-16 generic
AthlonXP 3200 (2.16 Ghz)
512 meg PC2700 DDR memory
AGP 4x nVidia 6200 256 meg, using the 9755/ nvidia-glx-new drivers from the repo's

I know it's not a screaming machine, but I'm having some serious perfromance issues with UT2004's DM Hyperblast 2. The rest of the game works great at 1280x1024 with low-mid quality settings, usually between 60-70 fps. 

Hyperblast-2 is absolutely unplayable at these settings. I had to crank all the settings to low at 640x480 to get a somewhat reasonably playable framerate, roughly 15-20 fps. I say "playable" because in single player I'm still able to hit the bad guy every now and then, on "easy" at least.

Does anyone have any idea what I could do to get this level to playable performance?

Some points to note:

Beryl/Compiz are not running in the background.

The rest of the levels I play in a session are fine (as fine as they can be considering the hardware), it's just Hyperblast that's giving me issues.

Hopefully someone has some pointers to help out?!??? I suppose I could boot into Windows and see what happens there....

---

### Post by psyopper on 2007-06-29
Bump - anyone have any suggestions at all?

---

### Post by Cappy on 2007-06-29
Try this:
> Ryan "icculus" Gordon (who did the Linux port for Epic) suggested opening up my ~/ut2004/System/UT2004.ini and changing VARSize=32 to VARSize=64 to see if that would help. That made a dramatic change. VARSize controls how much static geometry in megabytes can be cached in AGP memory.

---

### Post by psyopper on 2007-06-30
I gave it a shot, and it helped a little. By a little I mean about this ->||<- much...

Any other ideas out there? I may try tweaking the ini a little more to see what I can come up with.

---

### Post by psyopper on 2007-07-09
Turns out that while I do have an AGP card in an AGP slot I didn't actually have AGP enabled...

:)

Changed    

Option         "NvAGP" "1" 

to

Option         "NvAGP" "2"

in my xorg.conf

For those that don't know (or those following in my footsteps) NvAGP has 4 options:

1 - Use only NvAGP
2 -  if exists use AGPGART else use NvAGP
3 - if exists use NvAGP else use AGPGART
4 - Use only AGPGART

nVidia recommends on ther driver setup page for drivers newer than 82.xx (somewhere around there) that they recommend setting 2. It was around that time that AGPGART started properly detecting and using sideband addressing and fast writes and thus NvAGP was no longer necessary.

I had selected 1 thinking the NvAGP and my Nvidia card would work best together. Apparently they have removed NvAGP from the drivers at this point because it certianly wasn't working for me!

The level is still laggy, but is far more playable than before, like hovering around 30-40 FPS and dipping in the extremes to 15 FPS rather than the 10-ish FPS with dips to 2-5 FPS. I haven't had time to sit down and play it out completely yet (or test any of the other levels), I kind of lost interest in UT2K4 because of this, now I need to get interested again!

---

