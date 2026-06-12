---
title: "resolution error in some games"
date: 2009-12-13
forum: Gaming &amp; Leisure
---

### Post by alexdej on 2009-12-13
Hy. I installed some games from playdeb, and when I start Enemy Territory (for example), and my screen is black and my monitor warn me to change the resolution back to 1280x1024x70. What should I do to start the game(s) with this resolution ?
I have a 19" Phillips LCD, so my monitor should support many MANY resolutions. And my graphic card is Nvidia GF FX 5200 on 128 bits. I can hear the sound from the game, but I can't see anything.
What's the problem ? Can anybody help me please ? :-s
By the way.. I use Ubuntu Karmic with Gnome.
Help ! :|

---

### Post by hessiess on 2009-12-13
Its the way the applications were coded, The vast majority of the games on Linux are resolution dependent, meaning that they will only run at one resolution, commonly 1024*768. If the monitor does not support the resolution the game runs at, your out of luck. Your best bet would be seeing if there is a command line switch or configuration option to make the game run in a window.

> 
I have a 19" Phillips LCD, so my monitor should support many MANY resolutions.


This is a common misconception, LCD displays are ONLY capable of displaying ONE resolution, known as the native resolution. Other resolutions are `supported' by the monitor internally scaling the image to the native resolution before displaying it, which produces a blurry/pixalated/distorted image, or by simply refusing to display anything.

Resolution dependence is a big problem with Linux games currently, it is caused largely by the SDL graphics library which is resolution dependent, unless it is used with OpenGL. I am attempting to rectify, or at least raise awareness of this problem  with my resolution independent graphics engine, Quad-ren.

---

### Post by alexdej on 2009-12-13
Not all games with lower resolution than 1280*1024 works, but I have games on lower resolution that works. What's the difference ?
I really can't do NOTHING to work ?!

---

