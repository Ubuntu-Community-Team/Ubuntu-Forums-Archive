---
title: "Laggy Starcraft"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by joebanana on 2007-04-25
I installed Starcraft on Ubuntu 7.04. The game itself is quite laggy and almost unplayable(-nice 20 hasn't worked). I did some digging and found I need to install the right graphic drivers(any other suggestions). I was playing around with drivers (I think i tried restricted driver manager and also installing them with envy) but nothing worked. I even managed to crash X when installing some exotic drivers. Any suggestions I have radeon9500pro.
Starcraft is not much graphic and I find it hard not to work. But because its the only game I play from time to time  and I just hate installing those bad looking windows. :) Please help!!

---

### Post by tgm4883 on 2007-04-25
what does this tell you?

```
glxinfo | grep direct
```

---

### Post by joebanana on 2007-04-25
Terminal output:
direct rendering: Yes

---

### Post by Lord Illidan on 2007-04-25
Personally, I can tell you that ATi cards + Linux = bad news.

But all is not lost.

What other specs do you have? As in RAM and CPU?

---

### Post by joebanana on 2007-04-25
AMD 2,5GHz barton
512MB

I have heared that linux and ATI don't get along. But cmon Starcraft runs on 66Mhz proc and 4MB graphic card.There must be something I can do...

BTW thanks for quick replys

---

### Post by Lord Illidan on 2007-04-25
> **joebanana said:**
> AMD 2,5GHz barton
512MB

I have heared that linux and ATI don't get along. But cmon Starcraft runs on 66Mhz proc and 4MB graphic card.There must be something I can do...

BTW thanks for quick replys

First, can u run glxgears -printfps in a terminal and show us the output?

---

### Post by joebanana on 2007-04-25
Output:
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
-----------------------------------------------------------------
 glxgears -info:
GL_RENDERER   = Mesa DRI R300 20060815 AGP 1x x86/MMX+/3DNow!+/SSE TCL
GL_VERSION    = 1.3 Mesa 6.5.2
GL_VENDOR     = Tungsten Graphics, Inc.
GL_EXTENSIONS = GL_ARB_fragment_program.............
10234 frames in 5.0 seconds = 2046.656 FPS
10204 frames in 5.0 seconds = 2040.723 FPS
10445 frames in 5.0 seconds = 2088.850 FPS
........
I should note that as I said I have just reinstall ubuntu 7.04 and haven't install graphic drivers cuz I am open to suggestions what will work with starcraft. (as I said I tryed some exotic and crash my X). Also starcraft uses DirectX 5 in windows if thats of any help.

---

### Post by tgm4883 on 2007-04-25
Sounds like a wine config problem.  I dont use wine so hopefully someone will come along.

---

### Post by joebanana on 2007-04-25
What do u use?

---

### Post by tgm4883 on 2007-04-25
For the very  few windows things i have, i use vmware

---

### Post by Lord Illidan on 2007-04-26
Personally, I'd just install an Nvidia card. An FX5200 would be a nice upgrade...and it would work perfectly with linux, and not too expensive neither..ATI has already declared that they are not going to support Linux.

---

### Post by joebanana on 2007-04-26
I only play Starcraft and there must be some configuring issue cuz I remember back then when people were playing starcrat without 3D support. And I am not even convinced it is a graphic card or driver problem. So plz people who play sc in ubuntu share with us how it works, what you have done, what card u have, any advice for me. 
I find somewhere on internet something about I have to turn DGA  on. Where is this? Could this might be the problem?

---

### Post by joebanana on 2007-04-26
I note for any player having the same problem that ATI graphic card isn't the problem. Just today my friend installed it on his computer and he experienced the same problems. He owns Geforce 6200 and problem isn't ubuntu specific. He installed it on different linux(i now he has KDE).
If I find anything useful I will post it hear. Meanwhile if someone know what might be done please share it with us.

---

### Post by deathbyswiftwind on 2007-04-26
Id say its a wine issue. Try reconfiguring your wine and see if you cant get it to run a little better

```

winecfg

```

Look into the video tab. I have an ati 9600 and my wine games dont run bad. I have starcraft so Im gonna install it and see if I can give you any pointers. :)

---

### Post by deathbyswiftwind on 2007-04-26
I dunno man I have beryl running on the "ati" drivers and it seems to play just fine for me.

---

### Post by joebanana on 2007-04-27
thx for replying. Could you please tell me what drivers do u have, wine version and winecfg configuration cuz I have tried everything in winecfg. Have u tried sc in game? No laggy mouse? Smooth play? Cuz my was almost unplayable.

---

### Post by taipoh on 2007-04-27
> **joebanana said:**
> I installed Starcraft on Ubuntu 7.04. The game itself is quite laggy and almost unplayable(-nice 20 hasn't worked). I did some digging and found I need to install the right graphic drivers(any other suggestions). I was playing around with drivers (I think i tried restricted driver manager and also installing them with envy) but nothing worked. I even managed to crash X when installing some exotic drivers. Any suggestions I have radeon9500pro.
Starcraft is not much graphic and I find it hard not to work. But because its the only game I play from time to time  and I just hate installing those bad looking windows. :) Please help!!

Just to be clear it's nice -n -20, more negative is better.

Anyway, no linux drivers for ATI cards from about 9500 and newer support 8bit color (StarCraft) to my knowledge.  That means that Wine has to "upconvert" each pixel which is responsible for the slowdown.

There's no present solution, sorry.

---

### Post by jdong on 2007-04-27
Starcraft runs fine in WINE on my ATI Radeon x1400 mobility laptop, Core duo 1.66, 1GB RAM.

It also runs on a GeForce4 MX440, A64 3000+

Make sure Beryl or any other compositor isn't running... and performance should be okay. At least it was for me; ymmv.

---

### Post by joebanana on 2007-04-28
Well I don't know exactly what did the trick but sc is now running almost as good as in windows.(you can still fell it's in Linux, but it's totally playable) I know I updated wine to 0.9.36 and turned off desktop effects.

---

### Post by conjur3r on 2007-04-28
It's most definitely the disabling of the desktop effects!  It's common practice to turn off all fancy effects before playing a game.  By the way, you know that you cannot play multiplayer on wine right?

---

### Post by jdong on 2007-04-28
> **conjur3r said:**
> It's most definitely the disabling of the desktop effects!  It's common practice to turn off all fancy effects before playing a game.  By the way, you know that you cannot play multiplayer on wine right?

Yes, certainly Desktop Effects will drastically reduce overall 3D performance. Multiplayer/LAN works fine in Starcraft under WINE, but Battle.NET won't.

---

### Post by deathbyswiftwind on 2007-04-28
Hey thanks alot buddy. I tried it out just to mess around and now Im hooked again!!!!! I didnt play it in like 4 years and now im sucked back in :lolflag:

---

### Post by joebanana on 2007-04-28
Well my battle.net works. Didn't tweak anything special just usual wine install. Only thing that doesn't work is fonts on b.net but If you know SC as good as I you shouldn't have a problem.

---

### Post by conjur3r on 2007-04-29
> **joebanana said:**
> Well my battle.net works. Didn't tweak anything special just usual wine install. Only thing that doesn't work is fonts on b.net but If you know SC as good as I you shouldn't have a problem.

Interesting!  I'll give it another try as I haven't tried it recently.  You are running a newish version of wine (0.9.3x) ?

---

### Post by KillerKiwi on 2007-04-29
I'm pretty sure when I did do this (a while ago to be sure) the issue was the sound driver... I just changed it with winecfg

Note: I have an ATI card and it works fine ;)

---

### Post by Lord Illidan on 2007-04-30
Interesting that blizzard games work so well with wine...warcraft 3 works perfectly on my system..

---

