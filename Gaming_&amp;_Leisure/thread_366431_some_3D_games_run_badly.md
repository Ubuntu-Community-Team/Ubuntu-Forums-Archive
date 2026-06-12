---
title: "some 3D games run badly"
date: 2007-02-20
forum: Gaming &amp; Leisure
---

### Post by Dr. Z2A on 2007-02-20
I just recently installed Ubuntu 6.10 on my highest speced computer again. To my great happiness, I found that linux can now do 3D with my graphics card (a task it couldn't do a few months ago).  I have an Intel integrated 855GM/64MB card. I have been having a bunch of fun with Beryi and such, but it seems that when I try to play some 3D games they are playable but don't run as well as they do under Windows. Specifically I've noticed Nexuiz lags quite a bit (although I never tried Nexuiz under Windows). I have however run Unreal Tournament 2004 under Windows and it runs beautifully. When I installed it on linux it originally was extremely slow to the point of unplayability. I went into the settings and changed the rendering from OpenGL to Software and now it runs at a decent speed, but the graphics look horrible in comparison to how they looked under Windows (it also crashes occasionally but that probably doesn't have anything to do with the 3d rendering).  I have been running these without Beryl running.  I ran glxinfo and found that I do have direct rendering enabled.  I've also noticed that when running graphical applications (including Nexuiz and UT2k4) from command line I often get the following warning:
> libGL warning: 3D driver claims to not support visual 0x4b
This warning also came up when I ran glxinfo.  Can anyone tell me how to make these games run better under linux?

---

### Post by chalimac on 2007-02-21
Yes, same here. It's a problem of the i810 driver. It is not as advanced as the nvdia proprietary drivers people use to squeeze their graphics cards in linux.

I've read Feisty looks promising for Intel cards if they manage to include x.org 7.2. Some 20% speed increase was reported in x.org testing.

Could you post how many fps you get with:

glxgears -printfps

I get around 500 fps in a Pentium 1.7

---

### Post by Dr. Z2A on 2007-02-21
I got 424.557 FPS on a 1.5-GHz Celeron M 340.

---

### Post by MkfIbK7a on 2007-02-22
yes this probably has to do with the graphics driver your card is forced to use as it isnt the ideal, but who knows maybe it WILL be better in fiesty...

---

### Post by Dr. Z2A on 2007-04-21
sorry to revive an old thread, but I just upgraded to Feisty Fawn and noticed that xorg 7.2 was included.  So I went to play UT2k4 which still had the same problems with opengl rendering.  Nexuiz would get slow whenever enemies appeared on the screen but that was fixed when I set the bits per pixel to 16, changed the game to full screen, and changed the resolution to 640x480.  I ran glxinfo and consistently got around 630 fps.  The libgl warning doesn't come up anymore either.  I'm also have UT2k4 installed on an external harddrive, so I'm not sure if that might be the problem or not.  Can anyone help me out?

---

