---
title: "Going dual screen switches me to a software rasteriser."
date: 2009-06-14
forum: Desktop Environments
---

### Post by atimholt on 2009-06-14
I plugged in an extra CRT monitor I had lying around into my laptop, and went to **System>Preferences>Display **to turn on dual screen. Now even just moving a window around has terrible terrible clipping (barely noticeable unless you've just come from good graphics) and compiz has stopped working--even after turning the extra screen off from within the display settings.

compiz-check gives me this:
[B][FONT=Courier New]Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap... [ OK ]
 Checking for non power of two support... [ OK ]
 Checking for composite extension... [ OK ]
 Checking for FBConfig... [ OK ]
 Checking for hardware/setup problems... [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use[/FONT][/B]

So, I'd kind of like to have compiz working at the same time as a dual screen, but I'd probably settle for just getting it to work with a single screen again. I'm going to go ahead and try creating a new user, seeing if it works in a different setup.

[SIZE=1]p.s., just a little _anecdote_ for amusement's sake (i.e., this is what I've gone through so far, _but it obviously has no bearing on the problem at hand. Go ahead and ignore the following wall of text._) -- Awfully enough, my dad and I thought at first that it was Ubuntu 9.04's fault (I had done a clean install from 8.04), that it didn't have the right graphics card driver for bizarre mysterious reasons. I got my Dad to try to look for one online. We found source for the right driver, but we didn't want to go through the rigmarole of compiling, etc. So I reinstalled to 8.04, upgraded to 8.10, then upgraded to 9.04: I figured that in a direct upgrade, the uprading process wouldn't be so assinine as to actually erase the drivers I already had ;). Needless to say, I got compiz to work in 9.04, but as soon as I tried dual screens again, it stopped working, and I realized that it really had been working in 9.04 before, up until I did the dual screens.[/SIZE]

p.p.s, couldn't get the code block to work with the compiz-check output. Played around with it (did the square brackets need escaping? etc.) but couldn't make it work. Sorry:(

**EDIT: **I have partially solved the problem. Reading the book "Ubuntu pocket guide and reference" by Keir Thomas, there is a note stating that messing with dual screens can mess up your graphics. To solve, he says, you can boot into recovery mode and run 'xfix.' This restored compiz functionality, and compiz-check returns all 'OK's,' but dual screen has turned off. Plus, I think the windows may still be rendering a little slow, though this might be placoebic.
So I'd still like to get dual screen and compiz working simultaneously. Is it possible? If so, then what the heck happens when you get cube and/or expo going with the extended desktop, does it just look a little wonky? Is that an important question? (I doubt it).

---

