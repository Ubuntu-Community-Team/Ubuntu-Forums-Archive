---
title: "How do I set up my monitor"
date: 2009-03-25
forum: General Help
---

### Post by nheather on 2009-03-25
I set up Ubuntu today for the first time and am pretty impressed with it.

One thing I haven't worked out though, even after much Googling is how to set up my monitor.

It's a ViewSonic VX922 19" TFT being driven by a GeForce 8800 GTS.

The video card was picked up and I've installed the recommended nvidia driver okay.  The screen is running at 1280x1024 which is the native resolution of my monitor.

But the monitor wasn't detected so I guess this is why I only have two refresh rate options 50Hz and 51Hz.

I should point out that even though it is set to 50Hz I don't beleive it is running at that frequency (the flicker would be very discernable) - also if I go into the menu on the monitor itself it reports to be running at 60Hz.

But I'd like to run at 75Hz or higher.

So how do I set up my monitor in Ubuntu?

Any help or advice would be really appreciated.

Cheers,

Nigel

---

### Post by evilaim on 2009-03-25
This should be posted in Media & Video I believe.  Look at this thread:

[http://ubuntuforums.org/showthread.php?t=822937](http://ubuntuforums.org/showthread.php?t=822937)

---

### Post by shad0w_walker on 2009-03-25
To my knowledge, TFTs don't flicker. They display a static image until it is told to update, it doesn't refresh the whole screen at Xhz, just bits that have changed.

 [http://en.wikipedia.org/wiki/Refresh_rate#Liquid_crystal_displays](http://en.wikipedia.org/wiki/Refresh_rate#Liquid_crystal_displays)  That has more details on it than I care to put here, but I wouldn't worry about the refresh rate.

---

### Post by nheather on 2009-03-25
Many thanks, I'll try updating xorg.conf with that info.

Cheers,

Nigel

---

### Post by nheather on 2009-03-25
Okay, I have added the monitor definition to my xorg.conf and restarted my computer.

Doesn't seem to have had any effect.  When I try to change the screen resolution the only refresh frequencies available are still 50Hz and 51Hz.

I re-checked xorg.conf just to make sure that I had saved my changes - I had.

Is there anything else I need to do to make the updates take effect?

Cheers,

Nigel

---

