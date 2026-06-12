---
title: "Quake 4 with dual displays pse hlp"
date: 2005-11-06
forum: Gaming &amp; Leisure
---

### Post by TasKiNG on 2005-11-06
I have managed to get Kubuntu running on two monitors using an NVIDIA 6600GT graphics card.  I now have the problem that when I run **Quake 4** , half of it is on one monitor and half is on the other.

Any ideas guys 

Note: Quake 3 runs fine and comes up full screen on my primary display

Cheers

---

### Post by tokyovigilante on 2005-11-10
Hi, not sure if this will help, but might be a good place to start looking anyway (taken from the linux nVidia 1.0-7676 driver release notes - [ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-7676/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-7676/README.txt)

> Q. Can I play full screen games across both display devices?

A. Yes. While the details of configuration will vary from game to game, the
   basic idea is that a MetaMode presents X with a mode whose resolution is
   the bounding box of the viewports for that MetaMode. For example, the
   following:
   
       Option "MetaModes" "1024x768,1024x768; 800x600,800x600"
       Option "TwinViewOrientation" "RightOf"
   
   produce two modes: one whose resolution is 2048x768, and another whose
   resolution is 1600x600. Games such as Quake 3 Arena use the VidMode
   extension to discover the resolutions of the modes currently available. To
   configure Quake 3 Arena to use the above MetaMode string, add the following
   to your q3config.cfg file:
   
       seta r_customaspect "1"
       seta r_customheight "600"
       seta r_customwidth  "1600"
       seta r_fullscreen   "1"
       seta r_mode         "-1"
   
   Note that, given the above configuration, there is no mode with a
   resolution of 800x600 (remember that the MetaMode "800x600, 800x600" has a
   resolution of 1600x600"), so if you change Quake 3 Arena to use a
   resolution of 800x600, it will display in the lower left corner of your
   screen, with the rest of the screen grayed out. To have single head modes
   available as well, an appropriate MetaMode string might be something like:
   
       "800x600,800x600; 1024x768,NULL; 800x600,NULL; 640x480,NULL"
   
   More precise configuration information for specific games is beyond the
   scope of this document, but the above examples coupled with numerous online
   sources should be enough to point you in the right direction.

BTW, what sort of FPS do you get with the 6600GT? What does the rest of your rig look like?

---

### Post by TasKiNG on 2005-11-11
Thanks  tokyovigilante

thats given me some things to try.

I am running at 1280x1024 high detail. 
i get between 20 and 60 fps. 
Its a dual amd 2gig mobo ( K7D MSI )

Cheers

---

### Post by tokyovigilante on 2005-11-11
That's cool, it sounds like you need to use something like "1280x1024,NULL;" to disable one of your screens. 

Was just curious to see how the 6600GT performed, i'm putting together a gaming rig and trying to justify the extra $350 NZ for the 7800GT compared to the 6600GT. 

Good luck sorting out your spanning problem!

Ryan

---

