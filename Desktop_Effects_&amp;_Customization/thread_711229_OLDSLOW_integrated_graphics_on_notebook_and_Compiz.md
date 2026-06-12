---
title: "OLD/SLOW integrated graphics on notebook and Compiz ?"
date: 2008-02-29
forum: Desktop Effects &amp; Customization
---

### Post by Anton Chigurh on 2008-02-29
Hi,

I'm planning to buy a 400$ Notebook for university (more precisely: to have something to play with, when there's nothing else to do).

Those things always have intergrated, sometimes even no name Intel graphics like " Intel Graphics Media Accelerator 950". 

It's especially important to me Compiz runs smoothly(most effects enebled), so are there any special requirements to run Compiz ?

---

### Post by kevinatkins on 2008-02-29
Hi,

I've had some success running Compiz on a few notebooks with integrated graphics but it depends on the chipset... 

Successful so far: 

Feisty (7.04) on an el-cheapo Celeron 2GHz machine, AGP graphics upto 64mb shared Intel 845G graphics. This ran fine with 7.04, but I simply could not get 7.10 to install properly.

Gutsy (7.10) on a Toshiba Satellite 2410, nVidia GeForce 4 graphics, 32MB VRAM - ** NOTE ** I had to tell Compiz to ignore low video RAM (can't remember exactly how right now, sorry!) because on Gutsy with nVidia cards, anything below 64MB VRAM has Compiz turned off by default. But it does run just fine.

Unsuccessful:

Dell Inspiron 2500 - older P III 1GHz machine with Intel graphics... think it was the i810 chipset...

Hope this helps a bit!

---

### Post by Anton Chigurh on 2008-02-29
I searched the forums and the most common low budget chipset is the Intel x3100 which needs some tweaking but works, the compiz gstreamer bug can be fixed too.

I guess I get an Acer Aspire 4315-051G08Mi, it should run pretty fast...

---

