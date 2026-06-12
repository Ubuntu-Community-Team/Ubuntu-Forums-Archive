---
title: "Edges of windows and cube appear &quot;glitchy&quot;"
date: 2009-01-25
forum: General Help
---

### Post by dwnii on 2009-01-25
When I move windows, or rotate the cube, the edges appear in a way that I can only describe as "jagged", or "blinky".

Firstly, what is the proper tech word to describe this glitchiness?

And secondly, is there a way to fix this, or is it simply the graphics process power that my laptop possesses? (I use a toshiba sattelite with a core 2 duo, and one gig of RAM.  As far as I know, there is no special GPU present.

---

### Post by cdahmedeh on 2009-01-25
I think you are talking about 'aliasing'. Feel free to read the Wikipedia article about it : [http://en.wikipedia.org/wiki/Anti-aliasing](http://en.wikipedia.org/wiki/Anti-aliasing) . In short, aliasing happens when the computer tries to draw a diagonal line on the screen, but since pixels are aligned horizontally and vertically and are square, it is very hard to make a perfect diagonal line. Instead, you see this 'staircase' that looks like a diagonal line and it does look very ugly. In order to fix this problem, you must enable anti-aliasing, which is a filter that uses certain techniques to make the lines smoother. However, this takes alot of processing power and reduces performance on integrated video cards like yours. You can try the option, though I'm not sure how to enable on a chip like yours, that would someone else's job who is more experienced than I am.

---

### Post by Grishka on 2009-01-25
if you have an nvidia card, there are antialiasing settings in nvidia-settings.

---

### Post by rokstaEnSweden on 2009-07-28
Sorry for replying to such an old topic, but through numerous searches this was the only relevant one to my query. I am having the exact problem as the above poster. When moving windows around in linux they appear "glitchy" on the sides; the borders on the container become uneven and "blink" while moving windows.  This, while not a major problem, is slightly irritating. I've tried adjusting the display settings as I'm also running an integrated nVidia graphics card (8200) but it doesn't seem to do me any good. I've put the anti-aliasing and the scopic options up to the highest, but it changes nothing. Any ideas?  Btw, I just switched from vista to linux today so I'm pretty much a nubcake at this. Thanks for your help. Oh, and I'm also running a AMD 64 bit machine with 4gb of ram, if that helps. I am using the 64 bit version of ubuntu.

---

