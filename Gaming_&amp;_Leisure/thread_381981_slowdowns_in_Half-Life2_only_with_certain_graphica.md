---
title: "slowdowns in Half-Life2 only with certain graphical effects"
date: 2007-03-11
forum: Gaming &amp; Leisure
---

### Post by finite9 on 2007-03-11
I installed Feisty Fawn Herd 5 on a HP Pavilion dv9297ea with an nVidia 7600 Go 512MB card, Core2Duo 7200 & 2GB system RAM.  Installed nvidia-glx from the feisty repos.

I installed Wine 0.9.31 from RAOFs repo and installed Steam etc just fine.

Game starts in record time, initial scenes look great and all details are set to max settings in native widescreen resolution 1440x900.  It looks great.  I play the first scene and there is zero slowdown.  I runs amazingly smoothly even with max settings at such a high resolution.  Then disaster strikes...

I walk out of the train station into the City 17 'town square' and FPS drops like a stone, and the game jerks along like a wounded animal.  After a bit of walking around, I realise that it's only when I look at the sky (think it's the sun ray effects), that the FPS drops.  It's like that directx effect cannot be handled in hardware and it's dropping to software mode to display it!  I look in the video settings and sure enough, it says that my hardware is DirectX8.1 and software mode is 9.0.  I *know* that this is not true...it is a directx9 cars for sure.  Is this why FPS drops on certain dx9 effects?  Is this an issue with Wine not supporting dx9 yet or something?  Another issue is that the sky that causes the issue also display corruption sometimes and I get white blocks of various sizes appearing in the sky as I move around.

I suppose I can install hl2 in Vista to see if it reports dx8.1 for the card and if it has the same issue, but would still appreciate comments.

---

### Post by Mblackwell on 2007-03-11
Are you running it with Windows XP compatibility?

---

### Post by finite9 on 2007-03-11
what, Wine?  don't know.  How do I set that, and why would it make a difference?

---

### Post by finite9 on 2007-03-11
never mind...this post confirmed my suspicions as correct:

[http://www.ubuntuforums.org/showthread.php?t=252246&highlight=half-life+nvidia](http://www.ubuntuforums.org/showthread.php?t=252246&highlight=half-life+nvidia)

There is no dx9 support in Wine or Cedega.  Solution is to lower all settings to turn off all the pretty graphics :(

Wonder if forcing OpenGL will work though...

---

### Post by bastiegast on 2007-03-11
Actually, there is. Many games using dx9 run quite good (Oblivion for example). I've played the HL2: Lost coast demo with HDR effects, if I look into settings it says: Hardware dxlevel: 9, Software dxlevel: 9.

Maybe dx9 is not *really* supported but at least it should work. Try to run half life with -dxlevel 90, if it doesn't work, try -dxlevel 70 or 80 try fiddling around with settings.

---

### Post by finite9 on 2007-03-12
> **bastiegast said:**
> Actually, there is. Many games using dx9 run quite good (Oblivion for example). I've played the HL2: Lost coast demo with HDR effects, if I look into settings it says: Hardware dxlevel: 9, Software dxlevel: 9.

Maybe dx9 is not *really* supported but at least it should work. Try to run half life with -dxlevel 90, if it doesn't work, try -dxlevel 70 or 80 try fiddling around with settings.

Can you please tell me how to do this?  I tried passing -dxlevel 90 to steam.exe and didnt work.  I tried running the full command contained in the Steam desktop link, in a terminal, but replaced steam.exe with the full correct path to hl2.exe and tried passing -dxlevel 90 there but wine complained of missing filename.

---

