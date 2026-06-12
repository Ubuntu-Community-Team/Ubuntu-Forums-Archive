---
title: "Counter strike-grainy and slow"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by Yetirat on 2007-05-28
Hi all,

I just installed Linux yesterday. I managed to get Steam installed via Wine (what a great program). My next challenge is to try and get my CS running nice and smoothly again. At the moment its fairly slow and grainy or pixelated I guess you could say. Does anyone have any suggestions to help get it running a bit smoother?


Thanks

---

### Post by shavenlunatic on 2007-05-28
system specs?

---

### Post by Yetirat on 2007-05-28
Hi, sorry.

Its an AMD Athlon processor 3500+, 1 gig of RAM, NVidia 6200 graphics card.

---

### Post by shavenlunatic on 2007-05-29
make sure you have -opengl ot the end of your wine launch command

if i recall correctly (can't check right now as I'm in windows):

```
 wine steam.exe -opengl 
```

or whatever, just edit yo0ur steam launcher... this should bump up your performance a little

Try dropping the resolution a little (if you have it at or above 1024x768) and disabling a few of the graphics swanky stuff...  My system is only marginally better than yours and mine runs at around 60fps most of the time with reasonable graphics (i can live without some raindrop splash effects to get those few extra FPS :) )

hope this helps, come back for more if u don't get any further :)

also, [www.winehq.com](www.winehq.com)  - take a look at the CS:S section in there, if the above doesn't help, it may be a reported bug with a fix available :)

---

### Post by Brynster on 2007-05-30
the flag is 

```
wine steam.exe -gl
```

you can also add things like -dxlevel 80 for directX 8 emulation or dxlevel 90 for directx 9

have a play around see which gives you the best performance. also adding those to the launcher properties in steam will have the same effect.

---

### Post by lordhebe on 2007-05-30
The grainy-ness is probably because you're using software rendering, and put the flag in the launch options menu in steam, not in the shortcut (or terminal) for steam. Also the -gl flag is for Half-life 1 based games (CS,DOD,HL ect) and -dxlevel 90 etc is for Half life 2 based game (CSS, DODS, HL2 ect) You can also use the flag for a shortcut, but only if launching the game directly. So like (For counter strike 1.6) ```
wine steam.exe -applaunch 10 -gl
```

---

### Post by shavenlunatic on 2007-05-30
> **Brynster said:**
> the flag is 

```
wine steam.exe -gl
```

you can also add things like -dxlevel 80 for directX 8 emulation or dxlevel 90 for directx 9

have a play around see which gives you the best performance. also adding those to the launcher properties in steam will have the same effect.


erm, i wasnt talking about the internal steam CS launch options (of which -gl is one of them i believe) I was talking about thepoint which wine is loaded

i've just installed CS to text out some settings for best performance.. will report back

---

### Post by Yetirat on 2007-05-31
Nice one guys, thanks for your help, i'll give it a whirl and let you know how I got on.

---

