---
title: "Doom 3 &amp; intel gma 950"
date: 2007-06-07
forum: Gaming &amp; Leisure
---

### Post by mesmento on 2007-06-07
I've a problem with Doom 3 on my Vaio vgn c2s (intel gma 950 128 ram). Black traces appear, event all the options in the advanced options are low (they appear as soon as I move the mouse in the beginning of a level). Is there a problem with the linux drivers ? There is a screenshot : 

[[img]http://pix.nofrag.com/12/45/9ef30161099398172ea58084b939t.jpg[/img]](http://pix.nofrag.com/12/45/9ef30161099398172ea58084b939.html)

any idea ?

P.S. : sorry for my bad english :(

---

### Post by Grout58 on 2007-06-07
That defiantly looks like a driver issue.  I would try a different driver.

---

### Post by mesmento on 2007-06-07
Ok. I install the xserver-xorg-video-intel who replace xserver-xorg-video-intel. In my xorg.conf I replace i810 with intel.

Results :

Neverwinter Nights is much faster. Nexuiz is playable ! But the texture are the same.

Is there newer drivers ? Mybe I must wait the next release of ubuntu, or some updates.

---

### Post by hikaricore on 2007-06-07
Ubuntu has little/nothing to with the intel drivers.
Development on many intel drivers was stopped by intel a long time ago.

Some were taken up by the linux community, but progress has been slow.

---

### Post by mesmento on 2007-06-07
> Ubuntu has little/nothing to with the intel drivers.

Yes I know, I think simply of the 2.0 version of the drivers for the intel graphics cards in Gutsy. I can wait Gutsy or compile this version.

---

### Post by hikaricore on 2007-06-07
Well if you're not afraid run in a development environment, you can always use gutsy now.  ^_^

---

