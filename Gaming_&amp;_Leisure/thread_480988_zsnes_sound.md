---
title: "zsnes sound"
date: 2007-06-22
forum: Gaming &amp; Leisure
---

### Post by Evan Burchard on 2007-06-22
I'm getting static with znes sound.  I tried playing with the switches to no avail.  

I have a AD1981HD, and the latest alsa driver.  I'm running Dapper on a thinkpad z61m.  

Thanks

---

### Post by richardwad1 on 2007-06-22
I have the same problem in 640*480 resolution in zsnes. The sound clears up when I run it on something smaller. I have an embedded system, so I'm assuming it is caused by not having enough RAM on my system. How much Ram do you have? Is your pagefile/swap partition big enough?

---

### Post by Evan Burchard on 2007-06-22
I have a gig of ram, but I'm not sure how to detect my page file or swap partition.  My system monitor shows that the emulation is maxing out my processor... I don't know if that's pertinent though.

I tried a smaller resolution, but it didn't fix the problem.  It does make the games more challenging though...

---

### Post by dfreer on 2007-06-23
zsnes version 1.51 has libao support, which IMO has far better sound quality. However, only version 1.42 is available in the official repos (gutsy and debian unstable have zsnes 1.51). so you have several options:
(1) stick with 1.42, and try increasing the sampling rate to 48000 hz (generally helps sound quality, although if you ever want to post a sound bug to zsnes developer's they will want you to use the default sample rate). I believe there is a libsdl library you can download that will improve sound quality, maybe libsdl-oss? not quite sure of the exact name.
(2) compile the newest version of zsnes, making sure to grab all of the required developer libraries and compiling with ./configure --enable-libao --enable-release
(3) grab a precompiled package of zsnes 1.51 from "somewhere" around the internet *shameless plug*

EDIT: another tip would be to enable the FPS display by going to ZSNES > Misc > Misc Keys, and see what kind of FPS you are getting. Anything newer than a pentium III should run zsnes just fine, with ~25 being the lowest FPS I would consider acceptable before you start lagging hardcore, which might also affect sound.

---

### Post by po0f on 2007-06-23
> **dfreer said:**
> ... I believe there is a libsdl library you can download that will improve sound quality, maybe libsdl-oss? not quite sure of the exact name. ...

[libsdl1.2debian-oss](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libsdl1.2debian-oss&searchon=names&subword=1&version=all&release=all)

---

### Post by BigSilly on 2007-06-24
> **po0f said:**
> [libsdl1.2debian-oss](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libsdl1.2debian-oss&searchon=names&subword=1&version=all&release=all)


I had exactly the same problems you describe, and after I downloaded the above it sorted it all out. It definitely works.

---

### Post by MetalMusicAddict on 2007-06-24
Just a tip. There many soundcards that only support a certain sample rate. Changing the sample rate in Znes to 48kHz fixed my static.

---

### Post by Evan Burchard on 2007-06-24
Okay, so I downloaded the libsdl1.2debian-oss package, and it didn't fix my problem.  I also tried playing with the  full range of sampling rates.  That didn't work either.  

So, then I downloaded the source from zsnes (1.51) and compiled it with the./configure --enable-libao --enable-release tags.  That worked... mostly.  

As far as reducing static, the lower the sampling rate the better.  Anything above 22050 outputs the following to the terminal, most often on the 44kHz setting, less on the lower two, and I'm pretty sure never on 22050 or anything lower than that. 

This is the message:
ALSA: underrun, at least 0ms.


It isn't perfect, every once in a while, the music hangs, and it crashes every time I close it... grr.  Any help with those things would be awesome.  

Thanks


Edit:
If I run it full screen, these errors are more common.  Windowed, with the changes everyone suggested, these errors rarely occur, and actually, it seems to run okay at any sampling rate.

---

### Post by hawko on 2007-06-28
> **MetalMusicAddict said:**
> Just a tip. There many soundcards that only support a certain sample rate. Changing the sample rate in Znes to 48kHz fixed my static.

Me too!! Sweeeet

---

### Post by dfreer on 2007-06-29
> **Evan Burchard said:**
> Okay, so I downloaded the libsdl1.2debian-oss package, and it didn't fix my problem.  I also tried playing with the  full range of sampling rates.  That didn't work either.  

So, then I downloaded the source from zsnes (1.51) and compiled it with the./configure --enable-libao --enable-release tags.  That worked... mostly.  

As far as reducing static, the lower the sampling rate the better.  Anything above 22050 outputs the following to the terminal, most often on the 44kHz setting, less on the lower two, and I'm pretty sure never on 22050 or anything lower than that. 

This is the message:
ALSA: underrun, at least 0ms.


It isn't perfect, every once in a while, the music hangs, and it crashes every time I close it... grr.  Any help with those things would be awesome.  

Thanks


Edit:
If I run it full screen, these errors are more common.  Windowed, with the changes everyone suggested, these errors rarely occur, and actually, it seems to run okay at any sampling rate.

What's your framerate like when fullscreen & windowed? is it running at the full 60/60 most of the time? anywhere below around 25/60 generally causes sound to stutter, in my experience.

---

### Post by weeniewhite on 2007-07-11
I might be a little late but a way to stop this grrrchchchch is often just to kill esd(if present). You will probably have to be root so : sudo killall esd

and
schlock!

It always worked for me but then the gnome system sounds will not work so that you need to restart esd to make them work again.

$ esd -nobeeps


I don't really like this way to "debug" the sound. Installing libsdl1.2debian-esd gave me good results without having to kill esd.


I hope it helps and that I'm not too late :S

---

