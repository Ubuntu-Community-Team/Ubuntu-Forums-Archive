---
title: "Composite display corruption - NVidia"
date: 2007-02-22
forum: Desktop Environments
---

### Post by hornett on 2007-02-22
Does anybody have normal X composite (not Beryl/Compiz) fully working on Edgy with NVIDIA drivers?

It's almost 100% working for me with xfce's WM or with xcompmgr me except for two annoyances:

[LIST]
[*]New windows or menus are shown for about half a second full of screen garbage. It is like the new window is displayed before the buffer has been written to. There are often black diagonal lines visible, and sometimes the contents of old windows.

This visibly happens about only 50% of the time or less, but nevertheless it's quite annoying and ugly.


[*]One other bug which I have given up on ever being fixed is the autoscroll function of Firefox. A trail of scroller icons is left as the page moves up and down. This bug has been open literally years. IIRC, I reported it back on FC3.
[/LIST]

I'm using NVidia's binary drivers, version 9746. My card is a 5500 with 256MB dedicated memory which I think should be good enough for composite.

Any tips to resolve either would be much appreciated! I've been out of the eye-candy scene for a while :)

Cheers,

Andy.

---

### Post by kalik on 2007-03-30
Have you installed something like Envy to merge your nVidia graphics card with Ubuntu?  I had a few graphical problems (mainly scrolling issues where the screen would take forever to load/scroll) but Envy cleared that up for me.  I know that your issues aren't the same but just wondering if the solution could be.

---

### Post by hornett on 2007-04-03
It's some kind of scheduler problem I think. 

I was able to solve it for 90% of the times by building a vanilla kernel with full pre-emption and a 1000Hz timer. 

Not sure what the Ubuntu defaults are, but they seemed to be causing starvation issues on my computer...

It could also be a bug in 2.6.17 which has been sorted in 2.6.20 tho.

---

