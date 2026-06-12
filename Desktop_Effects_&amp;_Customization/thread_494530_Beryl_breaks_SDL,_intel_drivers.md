---
title: "Beryl breaks SDL, intel drivers"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by maddog39 on 2007-07-07
Hello all,

I just upgraded to edgy (i have really wierd CPU problems and I cant run kernels with SMP so been running Dapper and upgraded manualy) and I have Beryl running on my Intel 945 chipset (on a desktop not a laptop). But whenever I try to run an SDL application, in particular a game im developing, I just get a window that pops up with white empty space and none of the graphics seem to render, but it works fine if beryl is disabled. Does anyone have an idea as to what the problem might be?

Thanks!
-maddog39

---

### Post by hyperair on 2007-07-07
Beryl, Compiz, Desktop effects and whatnot, they all run using the graphic card features. This means that any complex 3d applications or games will never run fast or will just have all sorts of problems with Beryl running. So, here's a sort of rule until you go upgrade your graphic card: When playing/running 3d games/applications, turn off Beryl/Compiz/Desktop-effects

---

### Post by maddog39 on 2007-07-07
Well I obviously know that they dont run as fast, its sort of common sense. This application in particular doesnt use any OpenGL accleration at all its just a simple 2D game using strictly SDL and I dont get any video when I run it with beryl enabled. I do have a nvidia geforce 6500 but its in another windows box at the moment because i fixed it up for my dad and im barrowing it to play some of my retail games as I only run linux on my boxes. I was just curious if there was a workaround to get SDL to display video while Beryl or other 3D effects (such as avant) were enabled. By the way, im using AIGLX not XGL.

---

### Post by hyperair on 2007-07-07
Darn strange. I've never had any problem playing 2D games, like TuxTyping. I could even Planet Penguin Racer on my computer with nVidia GeForce 4 MX 440 (it's an ancient card) with Compiz running.

---

