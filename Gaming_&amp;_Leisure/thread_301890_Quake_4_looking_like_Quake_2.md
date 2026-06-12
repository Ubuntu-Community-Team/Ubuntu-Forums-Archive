---
title: "Quake 4 looking like Quake 2?"
date: 2006-11-17
forum: Gaming &amp; Leisure
---

### Post by Particle on 2006-11-17
Since ATI's drivers don't support hardware-rendered OpenGL on Vista yet (but will do a software emulation using a stripped-down OpenGL 1.4), I installed Ubuntu 6.10 to play my OpenGL games:  Quake IV and Doom 3.  Under the 1.4 emulation, the games were sluggish and looked terrible.  GLQuake got about 1fps, too.  I can't quite figure that one out.

Aaaaanyway, I have the same problem under Ubuntu.  I got fglrx installed and working with DRI, etc.  The game still looks like it's straight out of 1998.  So, I'm left to wonder if perhaps OpenGL doesn't work on the Radeon X1900 series cards yet under ANY of ATI's drivers or what?

I'd love to play Quake IV and Doom 3, but it's not turning out so hot.

---

### Post by dagrump on 2006-11-18
You might need to look at some of the how-to's & make sure your video card is configured properly, I think ATI cards might be a PITA to set-up. I have nvidia 7300gs?, running drivers from the repos & both games seem about as fast as they did under microslouth. And I haven't seen a BSOD yet.

---

### Post by Tuna-Fish on 2006-11-18
What does typing "fglrxinfo" print?

Sounds exactly like you are still using the other drivers... Perhaps something went wrong in the installation?

in any way, Q4 should run properly once everything is correctly set  up.

---

### Post by Particle on 2006-11-18
Quake 4 does run--it just looks like crap even on max settings.
 
Like I said, fglrx seems to be setup properly.  My provider is "Radeon X1900 Series" or whatever instead of the Mesa libraries.  DRI is working, too.

---

### Post by dmn_clown on 2006-11-18
> Quake 4 does run--it just looks like crap even on max settings.

Like I said, fglrx seems to be setup properly. My provider is "Radeon X1900 Series" or whatever instead of the Mesa libraries. DRI is working, too.

If the fglrx driver is setup properly then you've just discovered why people that have used GNU/Linux for any length of time have moved away from ATi chipsets and video cards...

...poor drivers and terrible support.

---

### Post by Particle on 2006-11-18
I've known that for a long time.  I have also noticed massive improvements in their drivers starting about a year ago.
 
Radeon 9700
Radeon X800XT PE
Radeon X1900XT
 
I've been using ATI cards on linux for some time now.  I've never run into this poor of a driver before, but it seems to be a problem for their X1900 series in Windows as well.  It will barely play D3D games and has no hardware OpenGL support.  If you aren't playing Oblivion or Source games, then it'll likely crash your machine while playing, even if it is a DX title.

---

### Post by ATAQ on 2006-11-19
I used ATI before and their drivers totally suck(ed), well back then anyways. I have a Nvidia 6600, and it works great with Quake IV, I would advise checking that the ATI prop driver is installed and starting with x, not vesa drivers.

---

### Post by Particle on 2006-11-19
For the third time:  it is.
 
I don't get any video with the vesa, ati, or radeon drivers.  If fglrx isn't at least loaded I get a blank screen or the system locks up.  I did get DRI enabled, etc, too.

---

### Post by curvedinfinity on 2006-11-20
> **Particle said:**
> For the third time:  it is.
 
I don't get any video with the vesa, ati, or radeon drivers.  If fglrx isn't at least loaded I get a blank screen or the system locks up.  I did get DRI enabled, etc, too.
If you are so sure that everything is setup correctly, why did you even ask here in the first place? Looks like you are just out of luck. :(

---

