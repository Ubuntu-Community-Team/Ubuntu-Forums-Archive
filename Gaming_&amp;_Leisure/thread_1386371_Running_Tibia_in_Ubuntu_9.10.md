---
title: "Running Tibia in Ubuntu 9.10"
date: 2010-01-20
forum: Gaming &amp; Leisure
---

### Post by Grayfoxra on 2010-01-20
Hey everyone! I'm new to Ubuntu and am having trouble with running the game Tibia. It has a linux version and I've tried using wine as well as the linux version. With wine I'm unable to get past 2 fps when running it, and it doesn't let me switch to Opengl. The linux version I have tried to run the StartTibia.sh file as well as ./Tibia. I get the following error:

WARNING: Application calling GLX 1.3 function "glXCreatePbuffer" when GLX 1.3 is not supported!  This is an application bug!
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  136 (XFree86-DRI)
  Minor opcode of failed request:  7 ()
  Resource id in failed request:  0x1a00008
  Serial number of failed request:  66
  Current serial number in output stream:  66

Previously, I tried installing the correct driver for my PC. I have a ATI Radeon 9000 series card, and I installed everything it required for the Proprietary Driver on the AMD website,  as well as a new kernel, X86Free, X11, X-Server, libc6, and many more. 

But the kernel would not install properly because it was always needing more files, and the same with X-Server. So the ATI Proprietary Driver wouldn't run because it couldn't find X-Server. After Reinstalling I'm trying again from scratch.

What I'm trying to say is I have no clue what I'm doing, and am wondering if there's a tutorial for the files I will need and how to install my Graphics Driver properly. Or at least to get the Driver I'm using to accept OpenGL and have faster FPS.  Please help, and Thank you for reading :D!

---

### Post by cariboo on 2010-01-21
Moved to Gaming & Leisure, you may get better answers here.

---

### Post by 5nak3 on 2010-01-21
hi there,

i'm not at home at the moment and thus am posting from my phone. Nonetheless, if I'm not mistaken the 9000 series card is no longer supported by the closed source ATI drivers.

in fact, just wondering do you have an integrated card or is a descrete card?

when i tried to run tibia on my ATI card back on 8.04 I found that I couldn't without much difficulty and even when i finanlly got it running i had to change the settings within the graphics tab to avoid distortion.

i've not tried ati closed source drivers since my card was last supported, which must be a couple of years now. so i do not know how good they are or even if they work with your card.

now my best piece of advice right now, short of going back to 8.04 and trying in that would be to get a cheap nvidia card if you can, and swap out the ati card.

---

