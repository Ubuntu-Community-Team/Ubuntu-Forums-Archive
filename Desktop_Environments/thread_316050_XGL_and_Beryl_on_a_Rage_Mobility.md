---
title: "XGL and Beryl on a Rage Mobility"
date: 2006-12-10
forum: Desktop Environments
---

### Post by lk_hltn on 2006-12-10
Hi

I have a compaq armada m700 running ubuntu edgy. I have installed the mach64 drivers for the Rage Mobility P/M AGP 2x and glxinfo says that direct rendering is enabled and glxgears work fine.

I followed [this]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL") guide to install xgl and beryl with no success. ](*,) 

Can someone please help me to get this working!

Thanks in advance.

---

### Post by Bronco200 on 2006-12-11
HeyHo,

i have the same problem.
Reason would be that XGL dosn't support DRI itself, as i could read at a German Ubuntu Forum.
So activated DRI is unforunately not the key for a working 3D-Desktop :( 

Bronco200

---

### Post by lk_hltn on 2006-12-11
Thanks Bronco200,

Are you saying that there is no way to get htis working? 

Sorry if I have missed something but I am a N00b. :confused: 

lk_hltn

---

### Post by Bronco200 on 2006-12-11
Hi,

sorry but i dont't know this at the moment. I searching for myself a way to running it.
I'm a neewbie at LINUX and Ubuntu, too. 
I think it could be possible with modifikations of the configuration within the MESA driver.
But in case it will run, i think it won't run satisfying.
Actually i get ~ 120 - 160 fps, with hardware 3D acceleration you might get many more frames.

Bronco

---

### Post by lk_hltn on 2006-12-11
This makes it look like it won't be possible.

[http://www.freesoftwaremagazine.com/node/1757](http://www.freesoftwaremagazine.com/node/1757)

"(*)Card models named Rage (128, Mobility, II, pro etc.) were either Mach64 2D chips with added functionalities (those don&#8217;t have a working DRI/DRM and are called with the &#8220;ati&#8221; driver) or &#8220;real&#8221; 3D chips (their DRI/DRM module is r128). 3D works with r128, but missing visuals make Compiz unable to load."

lk_hltn

---

### Post by Bronco200 on 2006-12-12
Hi,

ok, i searched yesterday up to 3 hours for a solution without success.
But after testing different 3D Screennsaver like Antspot, i wouldn't invest more time to solve the problem, because it runs with a not acceptable preformance at a nearly 100% loaded CPU.
So i think 3D Desktop also wouldn't run with a acceptable performance.

Bronco

---

### Post by lk_hltn on 2006-12-12
Thanks Bronco,

I agree. Thinking about it, it was probably a bit optamistic to think that it might ever run well enough.

lk_hltn

---

### Post by CalcProgrammer1 on 2007-04-29
I have a Rage 128 Mobility M3 in my IBM ThinkPad A21p.  I'm pretty sure it's a true 3d chip, because I play 3d games on it (in Windows) all the time and it runs decently.  I'm using the ATi driver, but it just whitescreens on me, I'll try the r128 driver and see what happens.  The screensavers lag at full screen (that may be because A21p has a 1600x1200 LCD) but it may be the CPU, I'll see.

Does anyone else have this card and have they gotten it to work with any form of 3d in Linux?

---

