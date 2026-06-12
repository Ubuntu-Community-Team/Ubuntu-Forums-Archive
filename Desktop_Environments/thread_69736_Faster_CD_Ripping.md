---
title: "Faster CD Ripping?"
date: 2005-09-27
forum: Desktop Environments
---

### Post by erik-the-red on 2005-09-27
My CD Burner is one made a few years back. It's a Lite-On 40x12x48 CDRW.

I remember reading from PC World that this was one of the poorer performers for CD ripping.

Still, is there any way I can increase its ripping speed through Sound Juicer? It's really, really slow, like 4x.

---

### Post by wmcbrine on 2005-09-27
First, of course, make sure DMA is enabled for the drive (it's not by default).

I can't speak to Sound Juicer, but I got a big speed boost in Grip by turning off paranoia, extra paranoia, scratch detection and repair. (It mostly didn't help anyway -- discs with problems were unrippable either way.)

---

### Post by erik-the-red on 2005-09-27
So, how can I make sure DMA *is* enabled?

---

### Post by MinoltaLuvR on 2005-09-27
[QUOTE=erik-the-red]So, how can I make sure DMA *is* enabled?[/QUOTE]

its rather easy.
from a terminal type the following in:
sudo  hdparm -d /dev/cdrom

that will tell you if DMA is enabled.
if its not follow these steps here:
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#speedupcddvdrom](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#speedupcddvdrom)

worked like a charm for me. my cd burning times are much much better.

cheers

---

