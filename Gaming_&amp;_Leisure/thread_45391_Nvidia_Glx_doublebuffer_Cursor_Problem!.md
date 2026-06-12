---
title: "Nvidia Glx doublebuffer Cursor Problem!"
date: 2005-06-29
forum: Gaming &amp; Leisure
---

### Post by Omnios on 2005-06-29
Have a cursor problem with nvidia double buffer in glx games and apps. I had this problem with Never Winter nights and just now in Plane Shift update but not in game. 

Opening GLX2D
Creating Context
Video driver GL/X version (direct renderer)
Visual ID: 0x00000021, 16bit TrueColor
R5:G6:B5:A0,
level 0, double buffered
NOTIFY: OpenGL renderer: GeForce2 MX/AGP/SSE2 (vendor: NVIDIA Corporation) version 1.5.3 NVIDIA 71.74
NOTIFY: Using windowed mode at resolution 640x480.
NOTIFY: Pixel format: Color: 16 Alpha: 0 Depth: 16 Stencil: 0 AccumColor: 16 AccumAlpha: 0 MultiSamples: 0
WARNING! Crystal Space performs better in 24 or 32 bit display mode!
 
 What happenes it the mouse kind of disapears and or slows with movent. 

 I have a XFX nvidia Gforce2 100/200 64 meg card.
tom@Main:~$ lsmod |grep -i agp
agpgart                31784  1 nvidia
tom@Main:~$

tom@Main:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          NVIDIA
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled
tom@Main:~$

tom@Main:~$  cat /proc/driver/nvidia/cards/0 Model:           GeForce2 MX 100/200
IRQ:             11
Video BIOS:      03.11.00.18.00
Card Type:       AGP
tom@Main:~$

 Any advise would be apreciated once I got this double buffer mouse problem licked my set up will be good as far as my card goes. Currently a few games are unplayable.

---

### Post by Omnios on 2005-06-30
K im having some issues with certain aspects of nvidia and some games. Most games work but so far I am having problems with NWN and Planeshift updater which leads me to believe there may be a cursor bug with certain nvidia settings. So far I can only point the finger two a double buffer problem but want to investigate it a bit more before I file a bug report. 

 Is anyone else having similar problems with certain games?

---

