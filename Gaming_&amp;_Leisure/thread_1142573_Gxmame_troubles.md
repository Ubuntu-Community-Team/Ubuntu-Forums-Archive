---
title: "Gxmame troubles"
date: 2009-04-29
forum: Gaming &amp; Leisure
---

### Post by nickstar on 2009-04-29
Hi Guys,

I read up as much as possible on this one before posting here. Unfortunately I've tried everything that I've read about on the boards getting gxmame (with xmame backend) to work on my laptop (ubuntu 8.04) but im still not getting any luck!

I've gotten gxmame to recognise my roms in the available list, but when I either try to load a rom through the console or through the gxmame gui, I keep hitting errors. A pop-up window reads "LIRC disabled", whilst my console shows

> 
nicholas@nicholas-laptop:~$ gxmame mslug3
** Message: Loading gamelist
** Message: Loaded 6166 roms by 720 manufacturers covering 32 years.
** Message: with 231 games supporting samples.
** Message: catver not loaded, using default values
/dev/js0: No such file or directory
** Message: No Joystick found

** (gxmame:14846): WARNING **: Couldn't find themed icon for "gxmame-sound-toolbar"
** Message: Performing quick check, please wait:
/dev/js0: No such file or directory



from what I can understand,

*LIRC is used for IR controls in Linux - so I can't really see its relevance here!
*the '/dev/js0: no joystick found' error shows no matter what I try. ive disabled joysticks, and ive even enabled them and changed the path to /dev/input/js - which is my actual joystick path! I've also omitted the '0' at the end of the joystick path, as recommended on the gxmame FAQ page.
*the gxmam-sound-toolbar one is a bit of a doozy to me. I haven't been able to find any info on it.

I don't know what ive done wrong here, and it might be a no-brainer to you guys, but if you could help me out id be really grateful!

cheers

nick

---

### Post by gnumoreno on 2009-04-30
Hey, did you find a solution for this? I'm having the same trouble... :(

---

### Post by nickstar on 2009-04-30
yeah I did actually...

I was so fixed on metal slug that I didnt even think about trying out a different ROM!!!! ehehe oops

so after trying out 1941 only to find that it works, I did some snooping around, and realised that you also need the 'neogeo' rom in your rom directory to get the metal slug series to work.

nonetheless, the only uncorrupt metal slug rom that ive found is 'metal slug x' happy gaming!

---

