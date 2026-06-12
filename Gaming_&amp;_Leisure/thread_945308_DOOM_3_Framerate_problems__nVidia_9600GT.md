---
title: "DOOM 3 Framerate problems / nVidia 9600GT"
date: 2008-10-12
forum: Gaming &amp; Leisure
---

### Post by dustint83 on 2008-10-12
ive searched through the board for threads about this, cant find anything so here goes......

i decided to install doom3 a walla go, everything works but its pretty much unplayable because of the 'pausing/skipping' issue im having.

the actual framerates are fine, (around 70-fps) but every second or two the game skips, i guess the best way to explain it would be if you were watching a streaming video and had a slow internet connection so the video would have to buffer for a second then continue playing

anyways, the closets thing i found to an explanation is that my graphics card is running out of memory, that cant be the case, im using a geforce 9600gt with 512mb, overclocked to 725gpu/1041mem (stock speeds have the same problem so it isnt the OC causing it) also ive played the game on ultra high settings on windows and its perfect, no hangs

i know everyone says glxgears isnt a good benchmark tool and i agree, but it outputs a fps rating around 5,500 for my system. somethings not right.....

specs are as follows:
cpu: amd64 4000+ 2.1Ghz x2
graphics: pci-e geforce 9600gt
ram: 2gb
hd space: 550gb
motherboard: nvidia
soundcard: x-fi
os: ubuntu 8.10 intrepid 32bit (problem occured on 8.04 as well)

with all that said, what can i do/check to start figuring out whats causing the slowdown? im pretty good with linux so throw some commands at me (been using it for years now, since the redhat days)

and thanks in advance

---

### Post by dustint83 on 2008-10-12
?

---

### Post by Naegling23 on 2008-10-13
could be a couple of things.  One thing I would point out is that your running a 9600gt and an athlon 4000.  Your processor might be your limiting factor in that setup.  Try turning the visuals down a bit and see if the skipping goes away.  Also, are you running any background processes?  Is compiz running?  Those could suck some resources away.  Are you skipping frames in any other games?

---

### Post by dustint83 on 2008-10-13
> **Naegling23 said:**
> could be a couple of things.  One thing I would point out is that your running a 9600gt and an athlon 4000.  Your processor might be your limiting factor in that setup.  Try turning the visuals down a bit and see if the skipping goes away.  Also, are you running any background processes?  Is compiz running?  Those could suck some resources away.  Are you skipping frames in any other games?


no, no skipping in any other games, actually everything else i have is maxed out in settings, 16af, 16aa
, 1680x1050 res, etc.......

ive tried compiz being both on and off during doom3 gameplay, made no difference at all

alsa set the game to the LOWEST possible settings, everything turned off in advanced effects, 640x480 res, low quality machine spec

same thing happens, its not a fps issue like i said before, its just like it is constantly caching files or the hard drive is working on something. i dont know. it ran fine in ultra settings on windows, i dont see why it would be any different in linux, especially THAT MUCH different, i could understand maybe if i had to drop down the resolution just a bit but it wont even run in the lowest possible environment.

thanks for taking time out to reply btw! i aprreciate it

---

### Post by Naegling23 on 2008-10-13
that weird...to be honest, the game runs better for me than it did in windows, so its not a linux vs. windows thing.

It might be in some setting or driver somewhere.  I guess try toggling some of the effects off in game and see if you can find one that gets rid of it...maybe there is something that is poorly supported by the nvidia driver.

---

### Post by dustint83 on 2008-10-13
> **Naegling23 said:**
> that weird...to be honest, the game runs better for me than it did in windows, so its not a linux vs. windows thing.

It might be in some setting or driver somewhere.  I guess try toggling some of the effects off in game and see if you can find one that gets rid of it...maybe there is something that is poorly supported by the nvidia driver.

are you using an nvidia card? is so do you have any custom things youve added to your xorg.conf?

btw ive tried the 177.76 driver and 177.80 driver, same thing happens with both. maybe ill give the official drivers a try and see if that helps

---

### Post by dustint83 on 2008-10-13
> **pinballwizard66 said:**
> this really is strange i have 8800gt with 177.80 drivers and doom is working better then on my friend's windows xp on same settings so its not a linux issue. tried reinstalling?

more than once, i even extracted the contents of the pk4 files to see if that made a difference. its not an issue wether or not my computer can handle it or not, i know it can run it on full settings, its just that theres something cuasing my system to 'stutter step' for lack of a better term. it even does it on the main menu of doom..............my mouse will skip frames when i move it around the screen

---

### Post by Brebs on 2008-10-14
Try putting in /etc/modprobe.conf
```
options nvidia NVreg_EnableMSI=1 NVreg_UsePageAttributeTable=0
```
Using MSI to stop sharing an interrupt, and disabling PAT makes the nvidia driver use MTRR.

You'll need to unload the nvidia module to have the change take effect.

Also [lock doom3 to 60hz](http://forums.gentoo.org/viewtopic.php?p=4014247#4014247) to increase smoothness.

---

### Post by dustint83 on 2008-10-14
> **Brebs said:**
> Try putting in /etc/modprobe.conf
```
options nvidia NVreg_EnableMSI=1 NVreg_UsePageAttributeTable=0
```
Using MSI to stop sharing an interrupt, and disabling PAT makes the nvidia driver use MTRR.

You'll need to unload the nvidia module to have the change take effect.

Also [lock doom3 to 60hz](http://forums.gentoo.org/viewtopic.php?p=4014247#4014247) to increase smoothness.

i dont have a modules.conf, i wondered why a few days ago when i was doing some tweaking

im running intrepid

edit: i added the option code to /etc/modules.d/options and applied the other things you mentioned, all it done was make my framerate goto about 200fps and my dude moves super fast. i know the refresh rate of 60 should limit the fps but it didnt

and also the jumpiness/pausing/skipping or whatever you want to call it is still there, so it wouldnt have fixed that anyway

thanks though

---

### Post by Brebs on 2008-10-14
You would need the display rate to be exactly 60hz. Run "xrandr" to see the available options, and set with "xrandr --rate 60" (if it shows e.g. 51hz then see [DynamicTwinView](http://forums.gentoo.org/viewtopic-t-528285.html)).

Anyway, use the normal [nvidia bug report](http://www.nvnews.net/vbulletin/showthread.php?t=46678).

---

### Post by dustint83 on 2008-10-15
> **Brebs said:**
> You would need the display rate to be exactly 60hz. Run "xrandr" to see the available options, and set with "xrandr --rate 60" (if it shows e.g. 51hz then see [DynamicTwinView](http://forums.gentoo.org/viewtopic-t-528285.html)).

Anyway, use the normal [nvidia bug report](http://www.nvnews.net/vbulletin/showthread.php?t=46678).

its not an nVidia bug, all my other games run perfectly fine. this has something to do with doom

i did do the refresh rate fix you mentioned though

---

