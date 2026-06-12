---
title: "Half Life 2 Performance Problems"
date: 2006-09-06
forum: Gaming &amp; Leisure
---

### Post by lou1998 on 2006-09-06
I am trying to play Half Life 2 with Wine 0.9.19.  I got Steam running just fine and am able to start up Half Life 2, but the framerate is terrible.  
I am on a AMD Dual Core 4600, 2 GB RAM, GeForce 7900GT so I don't think its a hardware issue.
Anyone know of any tricks I might have missed?

Thanks!

---

### Post by WalmartSniperLX on 2006-09-06
A) Linux drivers don't max ur card as well as win drivers
B) Wine must emulate an entire win system inside of linux. This causes a major loss in performance in high power apps like 3d games.

Thats all i know heh. I tried HL2 myself and it was horrible. :D

---

### Post by byoon on 2006-09-06
> **WalmartSniperLX said:**
> A) Linux drivers don't max ur card as well as win drivers
B) Wine must emulate an entire win system inside of linux. This causes a major loss in performance in high power apps like 3d games.

Thats all i know heh. I tried HL2 myself and it was horrible. :D

I ran across this thread and had to reply because both A and B are incorrect and just wanted to clarify.

A) The nVidia Linux drivers work just fine.  You can get decent, but not good, FPS in HL2 and CSS with Cedega (although I really don't like this software and would recommend against it for reasons I have posted in both the Ubuntu and Transgaming forums).  The reason why you don't match the FPS is not because of the driver, it is because HL2 and CSS use DirectX9 which is a Microsoft proprietary API and which is not yet implemented in Cedega or Wine.  When you pit an OpenGL app on Linux and Windows against each other, you will find that they are about equal (with some people showing that nVidia drivers on Linux being faster).

B) Wine Is Not an Emulator!  Thus the name, WINE!  Spell it out.  Say the words.  It is a passthrough API where the Windows API gets translated to Linux API calls.  There is no emulation.  The DirectX implementation in Cedega and Wine are not mature enough to handle all of the DirectX8&9 API.

---

### Post by tristan on 2006-10-10
I'm running the GOTY DVD version of HL2 under Wine 0.9.22. I had very little trouble getting it installed and running, but by default it ran very slowly (5-10fps). This is because the game assumed that my configuration would allow it to run nicely with high graphics defaults (and it probably would under windows). 

Using winecfg I run steam under windows 2000, and I disable pixel shaders (which don't work properly anyway - no pretty water reflections etc) and desktop double buffering. I start the game with -dxlevel 90, and then by basically switching everything over to low (models, textures, shader, shadows, no AA, bilinear filtering) , at 800x600, I can get >30fps most of the time in HL2 with a 2.6Ghz P4, 1Gb RAM and a 6600GT. This frame rate is perfectly playable. 

I think until Wine's DirectX support improves, with HL2/Wine you have 2 choices. 

1 - Jaw dropping graphics at slideshow framerates. 

2 - Turn the settings down and have decent framerates with still very pleasing graphics.

You might find things are different with Cedega, but I don't own it so can't comment.

I'd be interested to know what other people's HL2/Wine experiences are.

---

### Post by aidanr on 2006-10-10
i've tried cs:s and hl2 in wine before and they weren't even playable, cedega does a fair better job at cs:s, i haven't tried hl2 yet, but i presume it would be a lot better in cedega aswell, still that said while it's playable theres about a 30 fps drop playing it through cedega than in windows

---

