---
title: "firefox plays gif anims too fast"
date: 2006-08-03
forum: Desktop Environments
---

### Post by jfdill_2 on 2006-08-03
After some debugging, I have determined that firefox plays multi-frame gif animations too fast, without enough delay.  I noticed this because scrolling pages slows way down when I scroll past large gif animations like banner ads.  Yeah, I know all about about:config image.animation_mode that can be none or once to "solve" this problem.  Further, this problem also occurs with Epiphany, but not Opera or Konqueror, so I suspect it goes back to the underlying gecko rendering engine.  I'm also going to check it out on Windows, but haven't done so yet.

Is there any way to increase the delay / adjust the refresh rate on animated GIFs in Firefox?

---

### Post by dtfinch on 2006-08-04
I haven't noticed a speed problem, but I think I remember hearing that some gifs specify a very low frame delay, like 1ms between frames, causing browsers to just flip through them at the fastest rate they allow, which I think is higher with Firefox than IE. An animator only testing such gifs in IE might think they're fine, when actually they're going to be displayed at the fastest rate possible in other browsers.

---

