---
title: "ATI 3D Rage, GLX Possible?"
date: 2005-08-07
forum: Desktop Environments
---

### Post by jlacroix on 2005-08-07
I just built a computer for my wife out of spare parts. It doesn't have an AGP port, so I was unable to throw one of my nvidia cards into it. It has a built in video card, ATI 3D Rage. I tried the FGLRX (I think that was the name) driver and it didn't work, I don't think that driver was meant for ATI 3D Rage.

Has anyone got this video card to work with Ubuntu? Or even GLX enabled with this card?

---

### Post by Teroedni on 2005-08-07
I have an AGP 3D pro on an Ubuntumachine and it worked fine
However i havent installed fglrx on that so i dont know about the 3d stuff.

What is the problem with the card . Doesnt it work?
Or is the problem that you cant get glx to work??

---

### Post by jlacroix on 2005-08-07
Everything is fine, its just that opengl stuff, like the screen savers, are very slow. Also, games are slow too.

---

### Post by az on 2005-08-07
You should have hardware acceleration out of the box.  How much memory does it have?  You may need to run at 800x600, 16 bit to be able to use acceleration if it has something like 4 or 8 megs.  (remember back in the day?)

In that case, it is a limitation of the hardware, and not the driver's fault.

---

### Post by fuzzix on 2005-11-04
I'd be interested to find out what sort of frames are possible from this card - I'm at my brother's machine right now (I installed Breezy here yesterday) which has a 2x AGP 4MB ATi 3D Rage Pro Turbo on board. The PSU isn't beefy enough to power the spare PCI GeForce 2 I have (damn you, Dell :-x) so we're stuck with it. Is there an Xorg driver I should be using besides "ati" in the "Device" section?

When I run glxgears it goes very smoothly for about 2 seconds, then the cogs slow down and stutter badly - this is at 1024x768x32@85Hz, 640x480x16@85Hz and everything in between. There's no fps info echoed at all.

Here's xorg.conf and output of glxinfo:

[http://pastebin.com/417137](http://pastebin.com/417137)

I'm wondering about the "client glx vendor string" in glxinfo - should that be "ati" or is that just the case with proprietary modules like fglrx? If more info is required please ask.

Thanks.

---

### Post by missingxtension on 2006-09-26
well the best answer is going to be Utah-glx it says u can compile it at XCFE 4.2 with is what i use anyways, ive also read something about compiling Xorg with DRI suppport but to tell you the thruth that didnt work in FBSD and i doubt it will on ubuntu,But maybe ill switch over to Xfree and just use that the only problem is that ubuntu install with Xorg default and ive never really uninstalled Xorg from ubuntu then again u can always try the slimed out version of XP or make your own with NLITE if u have to have Q3A witch i have to


p.s.I got and AIW ATI Rage 128, but i dont understand why Utah-glx  is not already a part of Xorg

---

