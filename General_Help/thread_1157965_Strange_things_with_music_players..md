---
title: "Strange things with music players."
date: 2009-05-13
forum: General Help
---

### Post by cptrohn on 2009-05-13
Ok so here is what is happening.

In rhytmbox I can play every single music file in my collection...

BUT in Amarok and Songbird I can't play my wma's that I had saved from when I used windows...

I do have restricted extras installed from medibuntu....

To be honest I don't know why this would be, wouldn't it make sense that if it they all would play in one that they would play in all 3?

---

### Post by kostkon on 2009-05-13
*Rhythmbox* uses *Gstreamer* as its multimedia backend whereas *Songbird* and *Amarok* use *Xine*.

Thus, try to install the windows codecs package called *w32codecs* (or *w64codecs* for 64bit systems) that is offered by the [*Medibuntu* repository]("http://medibuntu.org/").

---

